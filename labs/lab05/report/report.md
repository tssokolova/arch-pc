---
## Front matter
title: "Отчёт по лабораторной работе 5"
subtitle: "Основы работы с Midnight Commander (mc). Структура программы на языке ассемблера NASM."
author: "Татьяна Соколова НММбд-03-24 "

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью работы является приобретение практических навыков работы в Midnight Commander. 
Освоение инструкций языка ассемблера mov и int.

# Задание

1. Установить Midnight Commander

2. Изучить стуктуру программ

3. Изучить файл in_out.asm

4. Дополнить программы по заданию.

# Теоретическое введение

Midnight Commander (или просто mc) — это программа, которая позволяет просматривать
структуру каталогов и выполнять основные операции по управлению файловой системой,
т.е. mc является файловым менеджером. Midnight Commander позволяет сделать работу с
файлами более удобной и наглядной.

Программа на языке ассемблера NASM, как правило, состоит из трёх секций: секция кода
программы (SECTION .text), секция инициированных (известных во время компиляции)
данных (SECTION .data) и секция неинициализированных данных (тех, под которые во
время компиляции только отводится память, а значение присваивается в ходе выполнения
программы) (SECTION .bss).

# Выполнение лабораторной работы

## Знакомство с Midnight Commander

Открываю Midnight Commander (рис. [-@fig:001]), с помощью клавишь со стрелками и Enter перехожу в каталог ~/work/arch-pc.
Далее нажимаю F7 и создаю каталог lab05 (рис. [-@fig:002]).

![Запуск Midnight Commander](image/01.png){ #fig:001 width=70%, height=70% }

![Создание каталога](image/02.png){ #fig:002 width=70%, height=70% }

При помощи touch создаю файл lab05-1.asm (рис. [-@fig:003])

![Создание файла lab05-1.asm](image/03.png){ #fig:003 width=70%, height=70% }

Открываю файл на редактирование клавишей F4, выбрираю редактор mcedit, пишу код программы из задания. (рис. [-@fig:005])

![Программа lab05-1.asm](image/05.png){ #fig:005 width=70%, height=70% }

Открываю файл на просмотр клавишей F3 и проверяю, что он содержит набранный код. (рис. [-@fig:006])

![Просмотр файла lab05-1.asm](image/06.png){ #fig:006 width=70%, height=70% }

Транслирую файл программы в объектный файл, выполняю компановку объектного файла, получился исполняемый файл программы. (рис. [-@fig:007])

![Запуск программы lab05-1.asm](image/07.png){ #fig:007 width=70%, height=70% }

## Подключение внешнего файла in_out.asm

Скачиваю файл in_out.asm и размещаю его в рабочем каталоге. (рис. [-@fig:008])
Для копирования используется клавиша F5.
Для перемещения используется клавиша F6.

![Копирование файла in_out.asm](image/08.png){ #fig:008 width=70%, height=70% }

Скопировала lab05-1.asm в lab05-2.asm. (рис. [-@fig:009])

![Копирование файла lab05-1.asm](image/09.png){ #fig:009 width=70%, height=70% }

Пишу код программы lab05-2.asm с использованием подпрограмм из
внешнего файла in_out.asm. (рис. [-@fig:010])

![Программа lab05-2.asm](image/10.png){ #fig:010 width=70%, height=70% }

Скомпилирую программу и проврю запуск. (рис. [-@fig:011])

![Запуск программы lab05-2.asm](image/11.png){ #fig:011 width=70%, height=70% }

В файле lab5-2.asm заменила подпрограмму sprintLF на sprint. 
Заново собрала исполняеый файл. (рис. [-@fig:012]) (рис. [-@fig:013])

![Программа в файле lab05-2.asm](image/12.png){ #fig:012 width=70%, height=70% }

![Запуск программы lab05-2.asm](image/13.png){ #fig:013 width=70%, height=70% }

Теперь после вывода строки она не завершается символом перехода на новую строку.

##  Задание для самостоятельной работы

Скопировала программу lab05-1.asm и изменила код, так чтобы она работала по следующему алгоритму:
(рис. [-@fig:014]) (рис. [-@fig:015])

* вывести приглашение типа “Введите строку:”;

* ввести строку с клавиатуры;

* вывести введённую строку на экран.

![Программа lab05-3.asm](image/14.png){ #fig:014 width=70%, height=70% }

![Запуск программы lab05-3.asm](image/15.png){ #fig:015 width=70%, height=70% }

Аналогично скопировала программу lab05-2.asm и изменила код, но теперь использовал подпрограммы из файла in_out.asm.
(рис. [-@fig:016]) (рис. [-@fig:017])

![Программа lab05-4.asm](image/16.png){ #fig:016 width=70%, height=70% }

![Запуск программы lab05-4.asm](image/17.png){ #fig:017 width=70%, height=70% }

# Выводы

Научились писать базовые ассемблерные программы. Освоили ассемблерные инструкции mov и int.
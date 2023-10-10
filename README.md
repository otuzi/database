# Домашнее задание к занятию «Базы данных»

---
### Легенда

Заказчик передал вам [файл в формате Excel](https://github.com/netology-code/sdb-homeworks/blob/main/resources/hw-12-1.xlsx), в котором сформирован отчёт. 

На основе этого отчёта нужно выполнить следующие задания.

### Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

Приведите решение к следующему виду:

Сотрудники (

- идентификатор, первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).

---

### Решение: 
Таблицы базы данных:

1. Сотрудники
- идентификатор (первичный ключ, serial)
- ФИО сотрудника (varchar(50))
- Оклад (numeric)
- Должность (varchar(50))
- Тип подразделения (varchar(50))
- Идентификатор структурного подразделения (внешний ключ, integer)
- Дата найма (date)
- Адрес филиала (varchar(100))
- Проект на который назначен (varchar(50))

2. Отделы
- идентификатор (первичный ключ, serial)
- Название отдела (varchar(50))

3. Подразделения
- идентификатор (первичный ключ, serial)
- Название подразделения (varchar(50))

4. Филиалы
- идентификатор (первичный ключ, serial)
- Название филиала (varchar(50))
- Адрес филиала (varchar(100))

5. Проекты
- идентификатор (первичный ключ, serial)
- Название проекта (varchar(50))

6. Должности
- идентификатор (первичный ключ, serial)
- Название должности (varchar(50))

7. Типы подразделений
- идентификатор (первичный ключ, serial)
- Название типа подразделения (varchar(50))

Типы данных:
- serial - автоинкрементируемое целое число
- varchar(50) - строка длиной до 50 символов
- numeric - числовой тип данных
- integer - целое число
- date - тип данных дата

Пример решения для таблицы "Сотрудники":
'''
Сотрудники (
  идентификатор_сотрудника serial PRIMARY KEY,
  ФИО_сотрудника varchar(100),
  Оклад numeric,
  идентификатор_должности integer REFERENCES Должности (идентификатор),
  идентификатор_типа_подразделения integer REFERENCES Типы подразделений (идентификатор),
  идентификатор_структурного_подразделения integer REFERENCES Подразделения (идентификатор),
  Дата_найма date,
  идентификатор_филиала integer REFERENCES Филиалы (идентификатор),
  идентификатор_проекта integer REFERENCES Проекты (идентификатор)
);
'''
В данном случае, добавлены ссылки на таблицы "Должности", "Типы_подразделений", "Структурные_подразделения", "Филиалы" и "Проекты" по соответствующим полям. Таким образом, все данные описываются с использованием ссылок на другие таблицы, что соответствует требованиям второй нормальной формы.

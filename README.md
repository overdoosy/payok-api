﻿# PayOk API для ваших проектов на Python!

Официальная документация: **https://payok.io/cabinet/documentation/doc_main.php**

## Как установить? 

```pip install payokioapi```

## Примеры кода

```python
from payokioapi import payok

api = payok.AuthPayOk("API_KEY", API_ID) # Сюда вставляете свой токен и айди

# Получение баланса

get_balance = api.Balance() # Возвращает баланс в json формате
print("Balance: ", get_balance['balance'])
print("Ref_balance", get_balance['ref_balance'])

# Получение транзакций

get_trans = api.Transaction(1234, 1, 1) # Первое значение - айди вашего магазина, второе значение - айди платежа, третье значение - отступы (также возвращает данные в json формате)
print(get_trans)

# Получение выплат

get_payout = api.PayOut(2, 1) # Первое значение - айди выплаты, второе значение - отступы (также возвращает данные в json формате)
print(get_payout)

# Создание выплат

cr_payout = api.POC(50, "card", "1234567890", "balance", "sberbank", "https://example.com/") # Первое значение - сумма выплаты, второе значение - метод выплаты, третье значение - реквизиты, четвертое значение - тип коммисии, пятое значение - банк спб для выплаты, шестое значение - вебхук (также возвращает данные в json формате)
print(cr_payout)

# Создание форм оплаты

cr_form_url = api.Pay(10, "123", 1234, "Описание товара", "SECRET_KEY") # Первое значение - сумма заказа, второе значение - номер заказа (можете выставить что угодно), третье значение - айди вашего магазина, четвертое значение - описание товара, пятое значение - секретный ключ магазина (возвращает URL)
print(cr_form_url)
```
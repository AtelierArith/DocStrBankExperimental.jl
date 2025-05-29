Add a new currency to the (global) currency list and return a unit for that currency. Prefer the `@usingcustomcurrency` macro, which leads to more clear code, whenever possible. This function takes three arguments: the symbol for the currency, a string description of the currency (following the conventions outlined in the documentation for `currencyinfo`), and an exponent representing the number of decimal points to describe the minor currency unit in terms of the major currency unit. Conventionally, the symbol used to describe custom currencies should consist of only lowercase letters.

```
btc = newcurrency!(:btc, "Bitcoin", 8)  # 1.00000000 BTC
```

Add a new currency to the (global) currency list and assign a variable in the local namespace to that currency's unit. Provide three arguments: an identifier for the currency, a string description of the currency (following the conventions outlined in the documentation for `currencyinfo`), and an exponent representing the number of decimal points to describe the minor currency unit in terms of the major currency unit. Conventionally, the identifer used to describe custom currencies should consist of only lowercase letters.

```
@usingcustomcurrency btc "Bitcoin" 8
10btc  # 10.00000000 btc
```

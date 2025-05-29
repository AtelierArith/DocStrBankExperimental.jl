```
ValidationException
```

IBANを生成するためのパラメータが検証に失敗したときにスローされます。問題のある値と一致するBBAN属性を報告します。

## 例

```julia
julia> iban_random(CountryCode = "GR", BankCode = "xxx")
ERROR: ValidationException value: "xxx"
invalid characters [IbanGen.BankCode]  
```

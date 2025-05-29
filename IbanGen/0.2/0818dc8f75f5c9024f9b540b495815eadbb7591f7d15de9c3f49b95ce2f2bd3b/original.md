```
ValidationException
```

Thrown when parameters to generate an IBAN fail validation. Reports the problematic value and the matching BBAN attribute

## Example

```julia
julia> iban_random(CountryCode = "GR", BankCode = "xxx")
ERROR: ValidationException value: "xxx"
invalid characters [IbanGen.BankCode]  
```

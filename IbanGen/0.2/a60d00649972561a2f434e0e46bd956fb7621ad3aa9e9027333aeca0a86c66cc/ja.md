```
iban(iban_str::String)::Dict{String,String}
```

提供された文字列を検証し、IBAN構造に解析します。     

## 例

```julia
julia> iban("BR9700360305000010009795493P1")
Dict{String,String} with 8 entries:
  "CountryCode"      => "BR"
  "CheckDigits"      => "97"
  "BranchCode"       => "00001"
  "AccountType"      => "P"
  "AccountNumber"    => "0009795493"
  "value"            => "BR9700360305000010009795493P1"
  "BankCode"         => "00360305"
  "OwnerAccountType" => "1"

```

```
iban_random(
    CountryCode::Maybe{String}=nothing,
    BankCode::Maybe{String}=nothing,
    AccountNumber::Maybe{String}=nothing,
    BranchCode::Maybe{String}=nothing,
    NationalCheckDigit::Maybe{String}=nothing,
    AccountType::Maybe{String}=nothing,
    OwnerAccountType::Maybe{String}=nothing,
    IdentificationNumber::Maybe{String}=nothing
)::Dict{String,String}
```

提供された属性に基づいてランダムなIBANを生成します。提供されていない属性については、（提供されたまたは生成された）国のルールに従ってランダムな値が使用されます。国に対して定義されていない属性は無視されます。

## 例

```julia
julia> iban_random()
Dict{String,String} with 6 entries:
  "CountryCode"   => "GR"
  "BranchCode"    => "7500"
  "AccountNumber" => "1HRB7OApF5ABTOYH"
  "value"         => "GR8410975001HRB7OApF5ABTOYH"
  "BankCode"      => "109"
  "CheckDigits"   => "84"

julia> iban_random(CountryCode = "GR", BankCode = "109")
Dict{String,String} with 6 entries:
  "CountryCode"   => "GR"
  "BranchCode"    => "2170"
  "AccountNumber" => "24wO2qBgz1ROP82L"
  "value"         => "GR26109217024wO2qBgz1ROP82L"
  "BankCode"      => "109"
  "CheckDigits"   => "26"

```

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

Generate a random IBAN subject to the provided attributes. For an attributes that is not provided, a random value will be used according to the rules of the (provided or generated) country. Attributes that are not defined for a country are ignored.

## Example

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

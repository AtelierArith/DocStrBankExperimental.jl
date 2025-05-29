```
iban(
    CountryCode::String,
    BankCode::String,
    AccountNumber::String,
    BranchCode::Maybe{String}=nothing,
    NationalCheckDigit::Maybe{String}=nothing,
    AccountType::Maybe{String}=nothing,
    OwnerAccountType::Maybe{String}=nothing,
    IdentificationNumber::Maybe{String}=nothing,
)::Dict{String,String}
```

Generate an IBAN based on the provided parameters.

## Example

```julia
julia> iban(CountryCode = "GB", BankCode = "NWBK", BranchCode = "601613",AccountNumber = "31926819")
Dict{String,String} with 6 entries:
  "CountryCode"   => "GB"
  "BranchCode"    => "601613"
  "AccountNumber" => "31926819"
  "value"         => "GB29NWBK60161331926819"
  "BankCode"      => "NWBK"
  "CheckDigits"   => "29"  
  
```

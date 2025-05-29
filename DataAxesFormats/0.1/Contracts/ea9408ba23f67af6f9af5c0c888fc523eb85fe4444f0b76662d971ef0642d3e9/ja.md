```
contractor(
    computation::AbstractString,
    contract::Contract,
    daf::DafReader;
    overwrite::Bool,
)::ContractDaf
```

`computation`のための`contract`を強制する`daf`データセットをラップし、既存の出力の`overwrite`を許可する可能性があります。

!!! note
    `contract`が出力を指定している場合、`daf`は`DafWriter`である必要があります。


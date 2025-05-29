```
contractor(
    computation::AbstractString,
    contract::Contract,
    daf::DafReader;
    overwrite::Bool,
)::ContractDaf
```

Wrap a `daf` data set to enforce a `contract` for some `computation`, possibly allowing for `overwrite` of existing outputs.

!!! note
    If the `contract` specifies any outputs, the `daf` needs to be a `DafWriter`.


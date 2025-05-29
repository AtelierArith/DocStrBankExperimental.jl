```
function_contract(func::Function[, index::Integer = 1])::Contract
```

Access the contract of a function annotated by [`@computation`](@ref). By default the first contract is returned. If the [`@computation`](@ref) has two contracts, you can specify the `index` of the contract to return.

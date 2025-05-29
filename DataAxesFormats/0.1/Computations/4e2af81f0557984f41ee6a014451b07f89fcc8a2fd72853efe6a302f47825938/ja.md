```
function_contract(func::Function[, index::Integer = 1])::Contract
```

[`@computation`](@ref)で注釈された関数の契約にアクセスします。デフォルトでは最初の契約が返されます。もし[`@computation`](@ref)に2つの契約がある場合、返す契約の`index`を指定できます。

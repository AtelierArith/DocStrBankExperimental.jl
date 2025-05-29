```
function removeIdsZeros(os::OpStrings{T}) where {T <: Number}
```

元の `OpStrings` からすべての "Id" 演算子を削除し、`coeff` が `Float64_threshold()` より小さい任意の `OpString` 項も削除した `OpStrings` を返します。

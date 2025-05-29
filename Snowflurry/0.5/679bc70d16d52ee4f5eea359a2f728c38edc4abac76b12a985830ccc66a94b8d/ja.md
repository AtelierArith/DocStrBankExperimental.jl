```
fock_dm(i::Int64, hspace_size::Int64)
```

ヒルベルト空間のサイズ `hspace_size` で定義されたフォック基底 `i` に対応する密度行列を返します。

```jldoctest
julia> dm = fock_dm(0, 2)
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im


```

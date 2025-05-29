```
spin_up(T::Type{<:Complex}=ComplexF64)
```

スピンアップ状態の `Ket` 表現を返します。

`Ket` はデフォルトで `ComplexF64` の型 `T` の値を格納します。

# 例

```jldoctest
julia> ψ = spin_up()
2-element Ket{ComplexF64}:
1.0 + 0.0im
0.0 + 0.0im


```

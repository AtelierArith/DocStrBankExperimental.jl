```
spin_down(T::Type{<:Complex}=ComplexF64)
```

スピンダウン状態の `Ket` 表現を返します。

`Ket` はデフォルトで `ComplexF64` の型の値を格納します。

# 例

```jldoctest
julia> ψ = spin_down()
2-element Ket{ComplexF64}:
0.0 + 0.0im
1.0 + 0.0im


```

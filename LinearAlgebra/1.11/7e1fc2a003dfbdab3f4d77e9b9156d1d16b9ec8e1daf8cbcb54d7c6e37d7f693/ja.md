```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

`G` とスカラー `r` を計算します。これにより、任意のベクトル `x` に対して

```
x[i1] = f
x[i2] = g
```

乗算の結果が

```
y = G*x
```

次の性質を持つようになります。

```
y[i1] = r
y[i2] = 0
```

詳細は [`LinearAlgebra.Givens`](@ref) を参照してください。

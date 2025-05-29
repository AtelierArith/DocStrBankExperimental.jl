```
JacobianConfig(F::Vector{Polynomial{T}}, [x::AbstractVector{S}])
```

多項式のベクトル `F` のヤコビアンを効率的に評価できるデータ構造です。`x` は `F(x)` の出力タイプを決定するためだけに使用されることに注意してください。

```
JacobianConfig(F::Vector{Polynomial{T}}, [S])
```

ベクトル `x` の代わりに、型を直接指定することもできます。

```
make_companion_matrix(a::F, α::F)::Matrix{F2} where F <: GaloisFields.AbstractGaloisField
```

有限体の要素とその原始根から伴随行列を生成します。

# 引数

  * `a::F`: 有限体の要素
  * `α::F`: フィールドの原始根

# 戻り値

  * `Matrix{F2}`: 伴随行列

# 例

```julia
F4, α = GaloisField(2, 2, :α)
A = make_companion_matrix(α, α)
```

```
make_companion_matrix(a::F)::Matrix{F2} where F <: GaloisFields.AbstractGaloisField
```

有限体の要素から伴随行列を生成します。

# 引数

  * `a::F`: 有限体の要素

# 戻り値

  * `Matrix{F2}`: 伴随行列

# 例

```julia
F4, α = GaloisField(2, 2, :α)
A = make_companion_matrix(α)
```

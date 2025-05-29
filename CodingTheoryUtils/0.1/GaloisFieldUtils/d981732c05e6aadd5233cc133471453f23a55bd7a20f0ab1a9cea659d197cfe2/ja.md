```
make_companion_matrix(g::Vector{F})::Matrix{F} where F <: GaloisFields.AbstractGaloisField
```

多項式の係数ベクトルから伴随行列を生成します。

# 引数

  * `g::Vector{F}`: 多項式の係数ベクトル（定数項を除く）

# 戻り値

  * `Matrix{F}`: 伴随行列

# 例

```julia
F2 = @GaloisField 2
g = [F2(1), F2(1)]  # x^2 + x + 1 の係数
A = make_companion_matrix(g)
```

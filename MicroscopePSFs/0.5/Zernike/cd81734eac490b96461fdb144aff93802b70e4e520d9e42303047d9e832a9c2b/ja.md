```
ZernikeCoefficients(n::Integer; T::Type{<:Real}=Float64)
```

ZernikeCoefficientsを`n`項で標準値に初期化して構築します。

# 引数

  * `n`: Zernike項の数
  * `T`: 係数の数値型（デフォルト: Float64）

# 戻り値

  * 大きさ[1] = 1で、他の項はすべてゼロの`ZernikeCoefficients`

# 例

```julia
# 最初の15のZernike項の係数を作成
zc = ZernikeCoefficients(15)

# 特定の数値型で係数を作成
zc = ZernikeCoefficients(10, T=Float32)
```

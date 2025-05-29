```
PAMR1{T<:AbstractFloat}<: PAMRModel
```

PAMR1オブジェクトを作成します。また、[`PAMR`](@ref)および[`PAMR2`](@ref)も参照してください。

# キーワード引数

  * `C::AbstractFloat=1.`: 攻撃性パラメータ。

# 例

```julia
model = PAMR1(C=0.02)
```

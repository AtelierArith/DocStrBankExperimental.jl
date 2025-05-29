```
PAMR2{T<:AbstractFloat}<: PAMRModel
```

PAMR2オブジェクトを作成します。また、[`PAMR`](@ref)および[`PAMR1`](@ref)も参照してください。

# キーワード引数

  * `C::AbstractFloat=1.`: 攻撃性パラメータ。

# 例

```julia
model = PAMR2(C=0.02)
```

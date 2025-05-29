```
dic(loglik::AbstractVector{<:Real})
```

DIC（Deviance Information Criterion）を計算します。

# 引数

  * `loglik::AbstractArray`: 事後対数尤度のベクトル

# 戻り値

  * `dic::Real`: DIC値

注意: DICは事後分布が近似的に多変量ガウスであると仮定し、過剰適合したモデルを選択する傾向があります。

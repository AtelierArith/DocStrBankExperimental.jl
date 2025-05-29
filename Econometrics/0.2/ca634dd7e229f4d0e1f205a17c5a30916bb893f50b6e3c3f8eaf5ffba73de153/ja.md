```
vcov(obj::EconometricModel)
vcov(obj::EconometricModel{<:LinearModelEstimators}, vce::VCE = obj.vce)
```

モデルの係数の分散共分散行列を返します。`vce`引数を使用すると、分散推定量を要求できます。

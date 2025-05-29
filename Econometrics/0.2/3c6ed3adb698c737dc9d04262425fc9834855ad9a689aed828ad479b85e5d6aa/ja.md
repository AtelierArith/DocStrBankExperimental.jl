```
stderror(obj::EconometricModel)
stderror(obj::EconometricModel{<:LinearModelEstimators}, vce::VCE = obj.vce)
```

モデルの係数の標準誤差を返します。`vce`引数を使用すると、分散推定量を要求できます。

```
DefaultOrthonormalBasis(𝔽::AbstractNumbers = ℝ, vs::VectorSpaceType = TangentSpaceType())
```

多様体上のタイプ `VST` のベクトル空間の任意の直交正規基底。これは通常、多様体に対して利用可能な最も高速な直交正規基底です。

型パラメータ `𝔽` は、基底ベクトルの線形結合において係数として使用される [`AbstractNumbers`](@ref) を示します。

# 参照

[`VectorSpaceType`](@ref)

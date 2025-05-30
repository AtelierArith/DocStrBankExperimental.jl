```
MeanToNatural(::Type{T})
```

平均パラメータ空間のパラメータを自然パラメータ空間にマッピングする変換関数を返します。分布の型 `T` に対する変換関数のシグネチャは `(params_in_mean_space, [ conditioner ]) -> params_in_natural_space` です。

関連情報: [`NaturalToMean`](@ref), [`NaturalParametersSpace`](@ref), [`MeanParametersSpace`](@ref), [`getmapping`](@ref)

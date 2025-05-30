```
NaturalToMean(::Type{T})
```

自然パラメータ空間のパラメータを平均パラメータ空間にマッピングする変換関数を返します。分布のタイプ `T` に対して、変換関数のシグネチャは `(params_in_natural_space, [ conditioner ]) -> params_in_mean_space` です。

関連情報: [`MeanToNatural`](@ref), [`NaturalParametersSpace`](@ref), [`MeanParametersSpace`](@ref), [`getmapping`](@ref)

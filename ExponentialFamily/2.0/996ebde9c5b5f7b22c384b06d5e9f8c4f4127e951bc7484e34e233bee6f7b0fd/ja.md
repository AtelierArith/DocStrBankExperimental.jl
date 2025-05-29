```
MeanToNatural(::Type{T})
```

分布のタイプ `T` に対して、平均パラメータ空間のパラメータを自然パラメータ空間にマッピングする変換関数を返します。変換関数のシグネチャは `(params_in_mean_space, [ conditioner ]) -> params_in_natural_space` です。

参照: [`NaturalToMean`](@ref), [`NaturalParametersSpace`](@ref), [`MeanParametersSpace`](@ref), [`getmapping`](@ref)

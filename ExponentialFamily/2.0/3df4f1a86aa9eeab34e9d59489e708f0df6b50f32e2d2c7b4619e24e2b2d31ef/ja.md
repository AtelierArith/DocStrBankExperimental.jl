```
MeanParametersSpace
```

平均パラメータ空間 `θ` を希望するパラメータ空間として指定します。`logpartition` や `fisherinformation` のような一部の関数は、希望するパラメータ空間を明確にするために追加の `space` パラメータを受け入れます。`map(MeanParametersSpace() => NaturalParametersSpace(), T, parameters, conditioner)` を使用して、タイプ `T` の分布の `parameters` と `conditioner` を平均パラメータ化から対応する自然パラメータ化にマッピングします。

関連情報: [`NaturalParametersSpace`](@ref), [`getmapping`](@ref), [`NaturalToMean`](@ref), [`MeanToNatural`](@ref)

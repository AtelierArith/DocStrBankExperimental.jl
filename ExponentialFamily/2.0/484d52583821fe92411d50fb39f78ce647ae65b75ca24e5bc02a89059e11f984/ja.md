```
NaturalParametersSpace
```

自然パラメータ空間 `η` を希望するパラメータ空間として指定します。一部の関数（`logpartition` や `fisherinformation` など）は、希望するパラメータ空間を明確にするために追加の `space` パラメータを受け入れます。`map(NaturalParametersSpace() => MeanParametersSpace(), T, parameters, conditioner)` を使用して、タイプ `T` の分布の `parameters` と `conditioner` を自然パラメータ化から対応する平均パラメータ化にマッピングします。

関連情報: [`MeanParametersSpace`](@ref), [`getmapping`](@ref), [`NaturalToMean`](@ref), [`MeanToNatural`](@ref)

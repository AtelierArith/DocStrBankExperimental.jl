```
rescale(r::AbstractDIDResult, scale::AbstractVector{<:Real}, subset=nothing)
rescale(r::AbstractDIDResult, by::Pair, subset=nothing)
```

DID結果`r`からの係数推定値を再スケールします。`scale`の要素の順序は係数の順序と一致する必要があります。`scale`の長さが係数の総数よりも小さい場合、変換後に残る係数を表すインデックスを指定するために`subset`を指定する必要があります。あるいは、[`apply`](@ref)と同様に`by`が指定されている場合、スケールは[`treatcells(r)`](@ref)の値に基づいて計算できます。この場合、`subset`が指定されていなくても治療係数のみが変換されます。より一般的な変換については[`lincom`](@ref)を参照してください。

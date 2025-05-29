```
currenttimestep(simdata::AbstractSimData)
```

[`AbstractSimData`](@ref) オブジェクトから現在のタイムステップを取得します。

これは `timestep` とは異なる場合があります。タイムステップが `Month` の場合、`currenttimestep` は特定の月の長さに対して `Seconds` を返します。

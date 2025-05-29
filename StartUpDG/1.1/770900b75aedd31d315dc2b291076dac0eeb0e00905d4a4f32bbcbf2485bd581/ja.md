```
RefElemData(elementType::Line, approxType::SBP, N)
RefElemData(elementType::Quad, approxType::SBP, N)
RefElemData(elementType::Hex,  approxType::SBP, N)
RefElemData(elementType::Tri,  approxType::SBP, N)
```

`Quad()`, `Hex()`, および `Tri()` 要素のための SBP 参照要素データ。

`Line()`, `Quad()`, および `Hex()` の場合、`approxType` は `SBP{TensorProductLobatto}` です。

`Tri()` の場合、`approxType` は `SBP{Kubatko{LobattoFaceNodes}}`、`SBP{Kubatko{LegendreFaceNodes}}`、または `SBP{Hicken}` である可能性があります。

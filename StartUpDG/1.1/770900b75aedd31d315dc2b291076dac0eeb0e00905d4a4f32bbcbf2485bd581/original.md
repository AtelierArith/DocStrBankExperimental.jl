```
RefElemData(elementType::Line, approxType::SBP, N)
RefElemData(elementType::Quad, approxType::SBP, N)
RefElemData(elementType::Hex,  approxType::SBP, N)
RefElemData(elementType::Tri,  approxType::SBP, N)
```

SBP reference element data for `Quad()`, `Hex()`, and `Tri()` elements. 

For `Line()`, `Quad()`, and `Hex()`, `approxType` is `SBP{TensorProductLobatto}`.

For `Tri()`, `approxType` can be `SBP{Kubatko{LobattoFaceNodes}}`, `SBP{Kubatko{LegendreFaceNodes}}`, or `SBP{Hicken}`. 

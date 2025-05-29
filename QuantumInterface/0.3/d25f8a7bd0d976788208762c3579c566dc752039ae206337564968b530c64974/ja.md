```
tensor(x::Basis, y::Basis, z::Basis...)
```

与えられた基底から[`CompositeBasis`](@ref)を作成します。

与えられたCompositeBasisは展開され、結果として得られるCompositeBasisは他のCompositeBasisを含まないようになります。

```
struct InferenceLattice{𝕃<:AbstractLattice} <: AbstractLattice
```

推論中の抽象解釈に使用される完全なラティス。基本ラティス `𝕃` を拡張し、`LimitedAccuracy` を付加します。

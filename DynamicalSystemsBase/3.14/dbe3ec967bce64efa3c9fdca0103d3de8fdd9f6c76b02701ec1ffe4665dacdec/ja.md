```
poincaresos(A::AbstractStateSpaceSet, plane; kwargs...) → P::StateSpaceSet
```

与えられたデータセットの与えられた `plane` のポアンカレ断面を計算し、ハイパープレーンを挟む点の間で線形補間を行います。

引数 `plane` とキーワード `direction, warning, save_idxs` は [`PoincareMap`](@ref) と同じです。

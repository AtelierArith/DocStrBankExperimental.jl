```
function nodevalues(nodevals, xgrid::ExtendableGrid{Tv,Ti}, UD::UserData; time = 0) where {Tv,Ti}
```

与えられたグリッドのデータ関数のノード値を持つ2D配列を返します。

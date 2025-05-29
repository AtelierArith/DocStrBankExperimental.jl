```julia
GetRealSpacePositions(uc::UnitCell{T} ; OffsetRange::Int64 = 2) --> Dict
```

指定された位置にある格子点のサブ格子および単位格子座標を与える値を持つ、キーがデカルト座標（`accuracy` 桁に丸められたベクトル）である辞書を返します。

```
isclose(::UnitRange{Int64}x, ::UnitRange{Int64}y, distance::Integer)
```

2つの範囲が近いかどうかをテストします。

distance == 0 の場合、これは isoverlapping() と同じです。distance == 1 の場合、これは istouching() と同じです。distance > 1 の場合、これは近さのテストです。

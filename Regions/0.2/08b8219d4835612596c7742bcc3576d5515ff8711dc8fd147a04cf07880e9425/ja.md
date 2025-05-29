```
isclose(a::Run, b::Run, x::Integer, y::Integer)
isclose(a::Run, b::Run, d::Integer)
isclose(x::Run, y::Run, distance::Vector[Int64])
```

2つのランが近いかどうかをテストします。

distance == 0 の場合、これは isoverlapping() と同じです。distance == 1 の場合、これは istouching() と同じです。distance > 1 の場合、これは近さのテストです。

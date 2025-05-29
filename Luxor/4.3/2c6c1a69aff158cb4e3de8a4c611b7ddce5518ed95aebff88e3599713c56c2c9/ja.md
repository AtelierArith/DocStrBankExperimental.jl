```
label(txt::T where T <: AbstractString, direction::Float64, pos::Point=O;
    offset=5,
    leader=false,
    leaderoffsets=[0.0, 1.0])
```

点にテキストラベルを追加し、その点に対して相対的に配置します。たとえば、`0.0`は東、`pi`は西です。

```julia
label("text", pi)          # 原点の左にテキストを配置します
```

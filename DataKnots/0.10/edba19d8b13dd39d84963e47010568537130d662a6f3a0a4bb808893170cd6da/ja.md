```
It :: AbstractQuery
```

クエリ式では、`It`を使用してクエリの入力を参照します。

```jldoctest
julia> unitknot[Lift(3) >> (It .+ 1)]
┼───┼
│ 4 │
```

`It`はクエリ合成に関する恒等性です。

```jldoctest
julia> unitknot[Lift('a':'c') >> It]
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

`It`は`Get`を使用したデータナビゲーションのための省略記法を提供します。したがって、`It.a.x`は`Get(:a) >> Get(:x)`と同等です。

```jldoctest
julia> unitknot[Lift((a=(x=1,y=2),)) >> It.a]
│ a    │
│ x  y │
┼──────┼
│ 1  2 │

julia> unitknot[Lift((a=(x=1,y=2),)) >> It.a.x]
│ x │
┼───┼
│ 1 │
```

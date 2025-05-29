```
linearspace(start::T, stop::T, N::Int)  where {T<:Number}
```

線形空間を生成します。

`start` と `stop` の間に `N` 個の数の線形列を生成します（すなわち、間に均等な間隔を持つ数の列）。

# 例

```
julia> linearspace(2.0, 3.0, 5)
2.0:0.25:3.0
```

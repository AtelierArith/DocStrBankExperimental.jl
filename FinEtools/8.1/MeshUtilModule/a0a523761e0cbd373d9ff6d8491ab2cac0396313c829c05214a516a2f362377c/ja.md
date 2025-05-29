```
gradedspace(start::T, stop::T, N::Int)  where {T<:Number}
```

二次元空間を生成します。

`start` と `stop` の間に `N` 個の数の二次元列を生成します。この列は、隣接する数の間隔が開始から終了まで線形に増加することに対応しています。

# 例

```
julia> gradedspace(2.0, 3.0, 5)
5-element Array{Float64,1}:
 2.0
 2.0625
 2.25
 2.5625
 3.0
```

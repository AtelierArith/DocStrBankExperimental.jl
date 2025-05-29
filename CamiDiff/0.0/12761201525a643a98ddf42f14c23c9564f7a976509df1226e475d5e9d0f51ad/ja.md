```
gridPos(rval::T, grid::Grid{T}) where T<:Number
```

近似グリッド位置は、条件 `grid.r[n] < rval` を満たす最大の整数 `n` として定義されます [`Grid`](@ref)。

#### 例:

次のように定義された4点の指数グリッドを考えます。

```
julia> grid = castGrid("exponential", 4, Float64; h = 0.1, rmax = 2.0);

julia> println(grid.r)
[0.0, 0.6012192107114549, 1.265669197778149, 2.0]
```

点 $r = 1.0$ の近似グリッド位置は $2$ です ($n = 2$); すなわち、$r = 1.0$ は $0.6012192107114549$ ($n = 2$) より大きいですが、 $1.265669197778149$ ($n = 3$) より小さいです。

```
julia> r = 1.0;

julia> n = gridPos(r, grid)
2
```

```
fracPos(n::Int, rval::T, grid::Grid{T}; ϵ = 1e-8, k = 7) where T<:Real
```

[`Grid`](@ref) の位置 `n` に関する分数グリッドオフセット。

#### 例:

次のように定義された4点の指数グリッドを考えます。

```
julia> grid = castGrid("exponential", 4, Float64; h = 0.1, rmax = 2.0);

julia> println(grid.r)
[0.0, 0.6012192107114549, 1.265669197778149, 2.0]
```

点 $r = 1.0$ は $n = 2$ のすぐ上に位置し、分数位置 $Δn = 0.6120806373655796$ です。

```
julia> r = 1.0;

julia> n = gridPos(r, grid)
2

julia> Δn = fracPos(n, r, grid);

julia> t = (n+Δn-1)*grid.h;

julia> grid.r0 * (exp(t)-1) ≈ r
```

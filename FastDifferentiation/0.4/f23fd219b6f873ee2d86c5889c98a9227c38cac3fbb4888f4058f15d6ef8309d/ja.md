```
differential(variables::Node...)
```

スカラー関数の`variables`に関する導関数を取る無名関数を返します。

# 例

```julia
julia> @variables t
t

julia> f = t^2
(t ^ 2)

julia> Dt = differential(t)      
#69 (generic function with 1 method)

julia> Dt(f)
(2 * t)

julia> Dt = differential(t,t)    
#69 (generic function with 1 method)

julia> Dt(f)
2
```

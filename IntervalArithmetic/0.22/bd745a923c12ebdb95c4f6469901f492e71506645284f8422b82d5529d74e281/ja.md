```
@interval(expr)
@interval(T, expr)
@interval(T, expr1, expr2)
```

式を通過し、関数の各引数を内部コンストラクタ[`atomic`](@ref)でラップします。

# 例

```jldoctest
julia> setdisplay(:full);

julia> @macroexpand @interval sin(1) # Float64がデフォルトの境界タイプ
:(sin(IntervalArithmetic.atomic(Float64, 1)))

julia> @macroexpand @interval Float32 sin(1)
:(sin(IntervalArithmetic.atomic(Float32, 1)))

julia> @interval Float64 sin(1) exp(1)
Interval{Float64}(0.8414709848078965, 2.7182818284590455, com)
```

```
(c::Circuit)(arg::Number; kwargs...)
(c::Circuit)(; kwargs...)
```

`c`のすべての[`FreeParameter`](@ref)を`kwargs`で指定された通りに修正し、クランプされたパラメータを持つ新しい回路を返します。`c`は変更されません。

`arg`が渡された場合、`kwargs`にリストされていないすべての`FreeParameter`の値は`arg`に設定されます。

# 例

```jldoctest
julia> α = FreeParameter(:alpha);

julia> θ = FreeParameter(:theta);

julia> circ = Circuit();

julia> circ = H(circ, 0);

julia> circ = Rx(circ, 1, α);

julia> circ = Ry(circ, 0, θ);

julia> circ = Probability(circ);

julia> new_circ = circ(theta=2.0, alpha=1.0);
```

`conductor(c::Cyc)`

は、`c∈ ℚ (ζₙ)` となる最小の正の整数 n を返します。

`conductor(a::AbstractArray)`

は、すべての要素が `ℚ (ζₙ)` にある最小の正の整数 n を返します。

```julia-repl
julia> conductor(E(6))
3

julia> conductor([E(3),1//2,E(4)])
12
```

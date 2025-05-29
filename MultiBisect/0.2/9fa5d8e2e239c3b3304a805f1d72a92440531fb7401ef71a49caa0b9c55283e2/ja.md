```
interpolate(rootfinder, BG::BisectionGrid{T, N}; threaded=false) where {T, N}
```

`BG`のすべてのブレッキングエッジに沿った根を計算します。

関数`rootfinder`は、エッジを受け取り根を返す任意のメソッドであり、例えば[`edgeroot`](@ref)、[`linearroot`](@ref)、または[`marchingsquares`](@ref)などです。

# 例

```jldoctest
julia> f(x) = 1 - sum(abs2, x); # 単位円

julia> BG = bisect(f, (0.0:1.0, 0.0:1.0); iterations=3);

julia> interpolate(marchingsquares, BG)
8-element Vector{Tuple{Float64, Float64}}:
 (0.875, 0.0)
 (0.875, 0.25)
 (0.875, 0.5)
 (0.75, 0.625)
 (0.0, 0.875)
 (0.25, 0.875)
 (0.625, 0.75)
 (0.5, 0.875)

julia> interpolate(edge -> linearroot(f, edge), BG)
8-element Vector{Tuple{Float64, Float64}}:
 (1.0, 0.0)
 (0.9642857142857143, 0.25)
 (0.8571428571428571, 0.5)
 (0.75, 0.65)
 (0.0, 1.0)
 (0.25, 0.9642857142857143)
 (0.65, 0.75)
 (0.5, 0.8571428571428571)

julia> interpolate(edge -> edgeroot(f, edge, Roots.ITP()), BG)
8-element Vector{Tuple{Float64, Float64}}:
 (1.0, 0.0)
 (0.9682458365518543, 0.25)
 (0.8660254037844387, 0.5)
 (0.75, 0.6614378277661477)
 (0.0, 1.0)
 (0.25, 0.9682458365518543)
 (0.6614378277661477, 0.75)
 (0.5, 0.8660254037844387)
```

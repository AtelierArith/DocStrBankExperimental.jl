```
quadratic_interpolation(ps::AbstractVector{<:StaticVector{D, <:Real}}, fs::AbstractVector{<:Real}) where D
```

Calculate quadratic interpolation based on input values.

# Examples

```jldoctest
julia> using QuadraticOptimizer, StaticArrays, Random

julia> Random.seed!(42);

julia> q = Quadratic{2}([2,1,3], [1,2], 2)
Quadratic{2, Int64, 3}([2, 1, 3], [1, 2], 2)

julia> ps = [@SVector rand(2) for _ in 1:6]
6-element Vector{SVector{2, Float64}}:
 [0.6293451231426089, 0.4503389405961936]
 [0.47740714343281776, 0.7031298490032014]
 [0.6733461456394962, 0.16589443479313404]
 [0.6134782250008441, 0.6683403279577278]
 [0.4570310908017041, 0.2993652953937611]
 [0.6611433726193705, 0.6394313620423493]

julia> quadratic_interpolation(ps, q.(ps))
Quadratic{2, Float64, 3}([1.9999999999997884, 0.999999999999996, 2.999999999999987], [1.0000000000001212, 2.0000000000000053], 1.999999999999966)
```

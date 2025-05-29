```
quadratic_fitting(ps::AbstractVector{<:StaticVector{D, <:Real}}, fs::AbstractVector{<:Real}) where D
```

Calculate quadratic fitting based on input values.

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

julia> quadratic_fitting(vcat(ps, ps), vcat(q.(ps).-1, q.(ps).+1))
Quadratic{2, Float64, 3}([2.000000000387182, 0.9999999999890256, 2.999999999972893], [0.9999999997884512, 2.0000000000207985], 2.000000000052808)
```

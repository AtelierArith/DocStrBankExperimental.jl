```
getpaduapoints([f::Function,], [T=Float64,] n)
```

evaluates the function `f` on the Padua points (of type `T`) for degree `n`.

If no function `f` is provided, `getpaduapoints` returns a matrix of the paduapoints, where the first and second column represent the x and y components respectively. If `f` returns a single value, `getpaduapoints` returns a `Vector{T}`. If `f` returns a tuple or other indexable iterable, `getpaduapoints` returns a Matrix{T} where the i-th column represents the i-th component function of `f` applied to all of the Padua points.

# Examples

```jldoctest
julia> getpaduapoints(2)
6×2 Matrix{Float64}:
  1.0   1.0
  1.0  -0.5
  0.0   0.5
  0.0  -1.0
 -1.0   1.0
 -1.0  -0.5

julia> getpaduapoints(Float32, 1)
3×2 Matrix{Float32}:
  1.0   1.0
  1.0  -1.0
 -1.0   0.0

julia> getpaduapoints(Float32, 2) do x, y; x*y; end
6-element Vector{Float32}:
  1.0
 -0.50000006
  0.0
 -0.0
 -1.0
  0.50000006

julia> getpaduapoints(2) do x, y; x*y, 5*x*y; end
6×2 Matrix{Float64}:
  1.0   5.0
 -0.5  -2.5
  0.0   0.0
 -0.0  -0.0
 -1.0  -5.0
  0.5   2.5
```

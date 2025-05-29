```
protect(term::T)
```

Create a [`Protected`](@ref) context for interpreting `term` (and descendents) during `apply_schema`.

Outside a [`@formula`](@ref), acts as a constructor for the singleton `Protected{T}`.

# Example

```jldoctest; setup = :(using Random; Random.seed!(1))
julia> d = (y=rand(4), a=[1:4;], b=rand(4));

julia> f = @formula(y ~ 1 + protect(a+b));

julia> modelmatrix(f.rhs, d)
4×2 Matrix{Float64}:
 1.0  1.91493
 1.0  2.19281
 1.0  3.77018
 1.0  4.78052

julia> d.a .+ d.b
4-element Vector{Float64}:
 1.9149290036628313
 2.1928081162458755
 3.7701803478856664
 4.7805192636751865
```

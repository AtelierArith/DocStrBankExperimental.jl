```
bs(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

Calculate a basis for B-splines. 

The keyword arguments include one of:

1. `df`, possibly in combination with `intercept`
2. `boundary_knots` and `interior_knots`
3. `knots`

# Arguments

  * `boundary_knots :: Union{Tuple{T,T},Nothing} = nothing`: boundary knots
  * `interior_knots :: Union{Array{T,1},Nothing} = nothing`: interior knots
  * `order :: Int = 4`: order of the spline
  * `intercept :: Bool = false`: bool for whether to include an intercept
  * `df :: Int = order - 1 + Int(intercept)`: degrees of freedom
  * `knots :: Union{Array{T,1}, Nothing} = nothing`: full set of knots (excluding repeats)
  * `centre :: Union{T,Nothing} = nothing)`: value to centre the splines
  * `ders :: Int = 0`: derivatives of the splines

# Examples

```jldoctest
julia> Splines2.bs(collect(0.0:0.2:1.0), df=3)
6×3 Array{Float64,2}:
 0.0    0.0    0.0  
 0.384  0.096  0.008
 0.432  0.288  0.064
 0.288  0.432  0.216
 0.096  0.384  0.512
 0.0    0.0    1.0  
```

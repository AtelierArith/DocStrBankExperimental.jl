```
is(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

Calculate a basis for I-splines. 

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
  * `ders :: Int = 0`: derivatives of the splines

# Examples

```jldoctest
julia> Splines2.is(collect(0.0:0.2:1.0), df=3)
6×3 Array{Float64,2}:
 0.0     0.0     0.0   
 0.1808  0.0272  0.0016
 0.5248  0.1792  0.0256
 0.8208  0.4752  0.1296
 0.9728  0.8192  0.4096
 1.0     1.0     1.0   
```

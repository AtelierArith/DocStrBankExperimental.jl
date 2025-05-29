```
is_(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

Calculate a basis for I-splines and return a function with signature `(x:: Array{T,1}; ders :: Int = 0)` for evaluation of `ders` derivative for the splines at `x`.

The keyword arguments include one of:

1. `df`, possibly in combination with `intercept`
2. `boundary_knots` and `interior_knots`
3. `knots`

# Arguments

  * `boundary_knots :: Union{Tuple{T,T},Nothing} = nothing`: boundary knots
  * `interior_knots :: Union{Array{T,1},Nothing} = nothing`: interior knots
  * `order :: Int = 4`: order of the spline
  * `intercept :: Bool = false`: bool for whether to include an intercept (column of ones). This behaviour is different to the splines2 package from R, where intercept=FALSE will drop the first spline term.
  * `df :: Int = order + Int(intercept)`: degrees of freedom
  * `knots :: Union{Array{T,1}, Nothing} = nothing`: full set of knots (excluding repeats)

# Examples

```jldoctest
julia> Splines2.is_(collect(0.0:0.2:1.0), df=3)(collect(0.0:0.2:1.0))
6×3 Array{Float64,2}:
 0.0     0.0     0.0   
 0.1808  0.0272  0.0016
 0.5248  0.1792  0.0256
 0.8208  0.4752  0.1296
 0.9728  0.8192  0.4096
 1.0     1.0     1.0   
```

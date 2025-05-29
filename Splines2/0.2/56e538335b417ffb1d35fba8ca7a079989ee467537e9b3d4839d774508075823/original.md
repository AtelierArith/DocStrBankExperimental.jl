```
ns_(x :: Array{T,1}; <keyword arguments>) where T<:Real
```

Calculate a basis for natural B-splines and return a function with signature `(x:: Array{T,1}; ders :: Int = 0)` for evaluation of `ders` derivative for the splines at `x`.

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

# Examples

```jldoctest
julia> Splines2.ns_(collect(0.0:0.2:1.0), df=3)(collect(0.0:0.2:1.0))
6×3 Array{Float64,2}:
  0.0       0.0        0.0     
 -0.100444  0.409332  -0.272888
  0.102383  0.540852  -0.359235
  0.501759  0.386722  -0.172481
  0.418872  0.327383   0.217745
 -0.142857  0.428571   0.714286
```

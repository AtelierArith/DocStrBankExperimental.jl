```julia
struct GeneralizedLogistic
```

Type representing a generalized logistic function with specific parameters `a`, `b` and `c`, used to approximate a PLR curve as a function of the (linear) `EbN0`. The approximating function takes the following form:

$$
f(E_bN_0) = (1 + exp(a ⋅ (E_bN_0 - b)))^{-c}
$$

Any instance of this type can be called with a single number `ebno` as input and returns the resulting approximated PLR value following the formula above.

# Fields

  * `a::Float64`
  * `b::Float64`
  * `c::Float64`

# Constructors

The sole constructor takes 3 input numbers representing the `a`, `b` and `c` parameters in this order.

# Examples

```jldoctest
julia> using TelecomUtils

julia> g = GeneralizedLogistic(3, 1.1, 1.2)
GeneralizedLogistic(3.0, 1.1, 1.2)

julia> g(1.3) # This is not ebno in db, but linear
0.287945071618515
```

See the `plr_fit_notebook.jl` notebook in the package root folder for example of fitting to real simulated data.

```
lmlovo(model::Function [, θ::Vector{Float64} = zeros(n)], data::Array{Float64, 2},
       n::Int, p::Int [; kwargs...])

lmlovo(model::Function, gmodel!::Function [, θ::Vector{Float64} = zeros(n)],
       data::Array{Float64,2}, n::Int, p::Int [; MAXITER::Int=200,
       ε::Float64=10.0^-4])
```

Fit the `n`-parameter model `model` to the data given by matrix `data`. The strategy is based on the LOVO function, which means that only `p` (0 < `p` <= rows of `data`) points are trusted. The Levenberg-Marquardt algorithm is implemented in this version.

Matriz `data` is the data to be fit. This matrix should be in the form

```
x11 x12 ... x1N y1
x21 x22 ... x2N y2
:
```

where `N` is the dimension of the argument of the model (i.e. dimension of `x`).

If `θ` is provided, then it is used as the starting point.

The signature of function `model` should be given by

```
model(x::Union{Vector{Float64}, SubArray}, θ::Vector{Float64})
```

where `x` are the variables and `θ` is a `n`-dimensional vector of parameters. If the gradient of the model `gmodel!`

```
gmodel! = (g::SubArray, x::Union{Vector{Float64}, SubArray},
           θ::Vector{Float64})
```

is not provided, then the function ForwardDiff.gradient! is called to compute it.  **Note** that this choice has an impact in the computational performance of the algorithm. In addition, if `ForwardDiff.jl` is being used, then one **MUST** remove the signature of vector `θ` from function `model`.

The optional arguments are

  * `MAXITER`: maximum number of iterations
  * `ε`: tolerance for the gradient of the function

Returns a [`RAFFOutput`](@ref) object.

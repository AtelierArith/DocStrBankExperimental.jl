```
raff(model::Function, data::Array{Float64, 2}, n::Int; kwargs...)

raff(model::Function, gmodel!::Function, data::Array{Float64, 2},
    n::Int; MAXMS::Int=1, SEEDMS::Int=123456789,
    initguess::Vector{Float64}=zeros(Float64, n),
    ε::Float64=1.0e-4, noutliers::Int=-1, ftrusted::Union{Float64,
    Tuple{Float64, Float64}}=0.5)
```

Robust Algebric Fitting Function (RAFF) algorithm. This function uses a voting system to automatically find the number of trusted data points to fit the `model`.

  * `model`: function to fit data. Its signature should be given by

    ```
    model(x, θ)
    ```

    where `x` is the multidimensional argument and `θ` is the `n`-dimensional vector of parameters
  * `gmodel!`: gradient of the model function. Its signature should be given by

    ```
    gmodel!(g, x, θ)
    ```

    where `x` is the multidimensional argument, `θ` is the `n`-dimensional vector of parameters and the gradient is written in `g`.
  * `data`: data to be fit. This matrix should be in the form

    ```
    x11 x12 ... x1N y1
    x21 x22 ... x2N y2
    :
    ```

    where `N` is the dimension of the argument of the model (i.e. dimension of `x`).
  * `n`: dimension of the parameter vector in the model function

The optional arguments are

  * `MAXMS`: number of multistart points to be used
  * `SEEDMS`: integer seed for random multistart points
  * `initialguess`: a good guess for the starting point and for generating random points in the multistart strategy
  * `ε`: gradient stopping criteria to `lmlovo`
  * `noutliers`: integer describing the maximum expected number of outliers. The default is *half*. *Deprecated*.
  * `ftrusted`: float describing the minimum expected percentage of trusted points. The default is *half* (0.5). Can also be a Tuple of the form `(fmin, fmax)` percentages of trusted points.

Returns a [`RAFFOutput`](@ref) object with the best parameter found.

```
generate_test_problems(datFilename::String, solFilename::String,
    model::Function, modelStr::String, n::Int, np::Int, p::Int;
    x_interval::Tuple{Float64, Float64}=(-10.0, 10.0),
    θSol::Vector{Float64}=10.0 * randn(n), std::Float64=200.0,
    out_times::Float64=7.0)

generate_test_problems(datFilename::String, solFilename::String,
    model::Function, modelStr::String, n::Int, np::Int, p::Int,
    cluster_interval::Tuple{Float64, Float64};
    x_interval::Tuple{Float64, Float64}=(-10.0, 10.0),
    θSol::Vector{Float64}=10.0 * randn(n), std::Float64=200.0,
    out_times::Float64=7.0)
```

Generate random data files for testing fitting problems.

  * `datFilename` and `solFilename` are strings with the name of the files for storing the random data and solution, respectively.
  * `model` is the model function and `modelStr` is a string representing this model function, e.g.

    ```
     model = (x, θ) -> θ[1] * x[1] + θ[2]
     modelStr = "(x, θ) -> θ[1] * x[1] + θ[2]"
    ```

    where vector `θ` represents the parameters (to be found) of the model and vector `x` are the variables of the model.
  * `n` is the number of parameters
  * `np` is the number of points to be generated.
  * `p` is the number of trusted points to be used in the LOVO approach.

If `cluster_interval` is provided, then generates outliers only in this interval.

Additional parameters:

  * `xMin`, `xMax`: interval for generating points in one dimensional tests *Deprecated*
  * `x_interval`: interval for generating points in one dimensional tests
  * `θSol`: true solution, used for generating perturbed points
  * `std`: standard deviation
  * `out_times`: deviation for outliers will be `out_times * std`.

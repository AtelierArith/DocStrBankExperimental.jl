```
stepwise(df; dv, iv, sv, dir, output, measure)
```

Perform forward or backward stepwise regression.

# Arguments

  * `df::DataFrame`: dataset
  * `dv::T`: name of the dependent variable
  * `iv::Vector{T}`: list of independent variables
  * `sv::T`: static variable that will be included to every model (dv ~ sv + sum(iv))
  * `dir::Symbol=:f`: direction of modeling:

      * `:f`: forward
      * `:b`: backward
  * `output::Bool=false`: if true, print the regression details
  * `measure::Symbol=:r2`: measurement used for assessing performance:

      * `:r2`: adjusted R²
      * `:aic`: Akaike’s Information Criterion
      * `:bic`: Bayesian Information Criterion
  * `acc::Symbol=:cpu`: use CPU (default) or GPU acceleration:

      * `:cpu`
      * `:cuda`
      * `:metal`
  * `alpha::Float64=0.05`: significance level
  * `checkp::Bool=false`: if true, variable is added to/kept in the model only if the model's P-value is less than the significance level set by `alpha`

# Returns

  * `best_model::Vector{T}`: list of variables in the best model

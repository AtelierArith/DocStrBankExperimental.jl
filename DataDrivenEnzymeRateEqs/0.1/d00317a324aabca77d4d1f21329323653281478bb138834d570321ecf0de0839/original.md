```
fit_rate_equation(
    rate_equation::Function,
    data::DataFrame,
    metab_names::Tuple{Symbol, Vararg{Symbol}},
    param_names::Tuple{Symbol, Vararg{Symbol}};
    n_iter = 20
```

)

Fit `rate_equation` to `data` and return loss and best fit parameters.

# Arguments

  * `rate_equation::Function`: Function that takes a NamedTuple of metabolite concentrations (with `metab_names` keys) and parameters (with `param_names` keys) and returns an enzyme rate.
  * `data::DataFrame`: DataFrame containing the data with column `Rate` and columns for each `metab_names` where each row is one measurement. It also needs to have a column `source` that contains a string that identifies the source of the data. This is used to calculate the weights for each figure in the publication.
  * `metab_names::Tuple{Symbol, Vararg{Symbol}}`: Tuple of metabolite names that correspond to the metabolites of `rate_equation` and column names in `data`.
  * `param_names::Tuple{Symbol, Vararg{Symbol}}`: Tuple of parameter names that correspond to the parameters of `rate_equation`.
  * `n_iter::Int`: Number of iterations to run the fitting process.

# Returns

  * `loss::Float64`: Loss of the best fit.
  * `params::NamedTuple`: Best fit parameters with `param_names` keys

# Example

```julia
using DataFrames
data = DataFrame(
    Rate = [1.0, 2.0, 3.0],
    A = [1.0, 2.0, 3.0],
    source = ["Figure 1", "Figure 1", "Figure 2"]
)
rate_equation(metabs, params) = params.Vmax * metabs.S / (1 + metabs.S / params.K_S)
fit_rate_equation(rate_equation, data, (:A,), (:Vmax, :K_S))
```

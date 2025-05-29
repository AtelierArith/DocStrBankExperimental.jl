Partial out variables in a Dataframe

### Arguments

  * `df`: A table
  * `formula::FormulaTerm`: A formula created using `@formula`
  * `add_mean::Bool`: Should the initial mean added to the returned variable?
  * `method::Symbol`: A symbol for the method. Default is :cpu. Alternatively,  :gpu requires `CuArrays`. In this case, use the option `double_precision = false` to use `Float32`.
  * `maxiter::Integer`: Maximum number of iterations
  * `double_precision::Bool`: Should the demeaning operation use Float64 rather than Float32? Default to true.
  * `tol::Real`: Tolerance
  * `align::Bool`: Should the returned DataFrame align with the original DataFrame in case of missing values? Default to true.

### Returns

  * `::DataFrame`: a dataframe with as many columns as there are dependent variables and as many rows as the original dataframe.
  * `::Vector{Int}`: a vector of iterations for each column
  * `::Vector{Bool}`: a vector of success for each column

### Details

`partial_out` returns the residuals of a set of variables after regressing them on a set of regressors. The syntax is similar to `reg` - but it accepts multiple dependent variables. It returns a dataframe with as many columns as there are dependent variables and as many rows as the original dataframe. The regression model is estimated on only the rows where *none* of the dependent variables is missing.  Finally, with the option `add_mean = true`, the mean of the initial variable is added to the residuals.

### Examples

```julia
using  RDatasets, DataFrames, FixedEffectModels, Gadfly
df = dataset("datasets", "iris")
result = partial_out(df, @formula(SepalWidth + SepalLength ~ fe(Species)), add_mean = true)
plot(layer(result[1], x="SepalWidth", y="SepalLength", Stat.binmean(n=10), Geom.point),
   layer(result[1], x="SepalWidth", y="SepalLength", Geom.smooth(method=:lm)))
```

```
register_bivariate(f, df1, df2, ddf11, ddf12, ddf22)
```

Register a bivariate function `f` to `ExaModels`, so that it can be used within objective and constraint expressions

# Arguments:

  * `f`: function
  * `df1`: derivative function (w.r.t. first argument)
  * `df2`: derivative function (w.r.t. second argument)
  * `ddf11`: second-order derivative funciton (w.r.t. first argument)
  * `ddf12`: second-order derivative funciton (w.r.t. first and second argument)
  * `ddf22`: second-order derivative funciton (w.r.t. second argument)

## Example

```jldoctest
julia> using ExaModels

julia> relu23(x) = (x > 0 || y > 0) ? (x + y)^3 : zero(x)
relu23 (generic function with 1 method)

julia> drelu231(x) = (x > 0 || y > 0) ? 3 * (x + y)^2 : zero(x)
drelu231 (generic function with 1 method)

julia> drelu232(x) = (x > 0 || y > 0) ? 3 * (x + y)^2  : zero(x)
drelu232 (generic function with 1 method)

julia> ddrelu2311(x) = (x > 0 || y > 0) ? 6 * (x + y) : zero(x)
ddrelu2311 (generic function with 1 method)

julia> ddrelu2312(x) = (x > 0 || y > 0) ? 6 * (x + y) : zero(x)
ddrelu2312 (generic function with 1 method)

julia> ddrelu2322(x) = (x > 0 || y > 0) ? 6 * (x + y) : zero(x)
ddrelu2322 (generic function with 1 method)

julia> @register_bivariate(relu23, drelu231, drelu232, ddrelu2311, ddrelu2312, ddrelu2322)
```

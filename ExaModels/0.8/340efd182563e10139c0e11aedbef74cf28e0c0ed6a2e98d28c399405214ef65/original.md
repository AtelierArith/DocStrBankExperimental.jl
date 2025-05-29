```
@register_univariate(f, df, ddf)
```

Register a univariate function `f` to `ExaModels`, so that it can be used within objective and constraint expressions

# Arguments:

  * `f`: function
  * `df`: derivative function
  * `ddf`: second-order derivative funciton

## Example

```jldoctest
julia> using ExaModels

julia> relu3(x) = x > 0 ? x^3 : zero(x)
relu3 (generic function with 1 method)

julia> drelu3(x) = x > 0 ? 3*x^2 : zero(x)
drelu3 (generic function with 1 method)

julia> ddrelu3(x) = x > 0 ? 6*x : zero(x)
ddrelu3 (generic function with 1 method)

julia> @register_univariate(relu3, drelu3, ddrelu3)
```

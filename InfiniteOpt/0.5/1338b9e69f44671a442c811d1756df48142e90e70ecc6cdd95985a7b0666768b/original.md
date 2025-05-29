```
set_all_derivative_methods(model::InfiniteModel, 
                           method::AbstractDerivativeMethod)::Nothing
```

Sets the desired evaluation method `method` for all the derivatives currently added  to `model`. Note that this is done with respect to the infinite parameters. Errors  if a generative method is specified and the model contains dependent parameters.

**Example**

```julia-repl
julia> set_all_derivative_methods(model, OrthogonalCollocation(2))

```

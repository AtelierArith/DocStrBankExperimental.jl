```
lsrtm_objective!(G, model, source, dobs, dm; options=Options(), nlind=false)

Evaluate the least-square migration (data-space) objective function. Returns the function value and assigns in-place \
```

the gradient to G. `model` is a `Model` structure with the current velocity model and `source` and `dobs` are the wavelets and 
observed data of type `judiVector`.

# Example

```
function_value = lsrtm_objective!(gradient, model, source, dobs, dm; options=Options(), nlind=false)
```

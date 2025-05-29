```
lsrtm_objective(model, source, dobs, dm; options=Options(), nlind=false)
```

Evaluate the least-square migration objective function. Returns a tuple with function value and 
gradient. `model` is a `Model` structure with the current velocity model and `source` and `dobs` are the wavelets and 
observed data of type `judiVector`.

# Example

```
function_value, gradient = lsrtm_objective(model, source, dobs, dm)
```

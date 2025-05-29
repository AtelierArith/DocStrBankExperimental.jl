```
fwi_objective(model, source, dobs; options=Options())

Evaluate the full-waveform-inversion (reduced state) objective function. Returns a tuple with function value and vectorized \
```

gradient. `model` is a `Model` structure with the current velocity model and `source` and `dobs` are the wavelets and 
observed data of type `judiVector`.

# Example

```
function_value, gradient = fwi_objective(model, source, dobs)
```

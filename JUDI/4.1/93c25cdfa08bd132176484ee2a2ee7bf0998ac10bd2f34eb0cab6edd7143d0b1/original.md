```
twri_objective(model, source, dobs; options=Options(), optionswri=TWRIOptions())
```

Evaluate the time domain Wavefield reconstruction inversion objective function. Returns a tuple with function value and 
gradient(s) w.r.t to m and/or y. `model` is a `Model` structure with the current velocity model and `source` and `dobs` are the wavelets and 
observed data of type `judiVector`. Example =======     function*value, gradient = fwi*objective(model, source, dobs)

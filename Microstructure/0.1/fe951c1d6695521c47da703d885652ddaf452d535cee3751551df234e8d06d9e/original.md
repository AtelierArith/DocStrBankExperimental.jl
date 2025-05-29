```
increment!(
    model::BiophysicalModel,
    pairs::Tuple{Vararg{Pair{String, <:Any}}},
    ranges::Tuple{Vararg{Tuple{Float64, Float64}}}
)
```

Increment model estimates in place and return outliers by checking prior ranges. `model`: a biophysical model; `pairs`: paras of fields/subfiedls and values to add; fieldname => value2add; `ranges`: prior range.

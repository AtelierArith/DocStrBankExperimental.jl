```
imas2json(@nospecialize(ids::Union{IDS,IDSvector}), filename::AbstractString; freeze::Bool=false, strict::Bool=false, indent::Int=0, kw...)
```

Save the IMAS data structure to a JSON file with given `filename`.

# Arguments

  * `freeze` evaluates expressions
  * `strict` dumps fields that are strictly in ITER IMAS only
  * `kw...` arguments are passed to the `JSON.print` function

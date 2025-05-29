```julia
get_metabolite_from_chebi(cid::Int64; should_cache) -> Any

```

Get metabolite data corresponding to the ChEBI id `cid`. This function is cached automatically by default, use `should_cache` to change this behavior.

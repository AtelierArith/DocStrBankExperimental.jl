```julia
get_metabolite_from_metanetx(
    id::String;
    should_cache
) -> Any

```

Get metabolite data corresponding to the MetaNetX id `id`. This function is cached automatically by default, use `should_cache` to change this behavior.

```
AmbiguousIdentifier(identifier::Union{String, UUID}, matches::Vector, [collection])
```

Searching for `identifier` (optionally within `collection`), found multiple matches (provided as `matches`).

# Example occurrence

```julia-repl
julia> d"multimatch"
ERROR: AmbiguousIdentifier: "multimatch" matches multiple data sets
    ■:multimatch [45685f5f-e6ff-4418-aaf6-084b847236a8]
    ■:multimatch [92be4bda-55e9-4317-aff4-8d52ee6a5f2c]
Stacktrace: [...]
```

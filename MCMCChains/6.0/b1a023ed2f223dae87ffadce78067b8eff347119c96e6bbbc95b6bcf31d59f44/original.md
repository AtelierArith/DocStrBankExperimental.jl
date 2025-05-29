```
group(chains::Chains, name::Union{AbstractString,Symbol}; index_type::Symbol=:bracket)
```

Return a subset of the chain containing parameters with the same `name`, but a different index.

Bracket indexing format in the form of `:name[index]` is assumed by default. Use `index_type=:dot` for parameters with dot  indexing, i.e. `:sym.index`.

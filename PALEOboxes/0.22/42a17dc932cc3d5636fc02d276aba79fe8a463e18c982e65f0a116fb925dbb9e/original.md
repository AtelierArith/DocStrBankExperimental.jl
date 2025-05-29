```
get_domain(model::Model, name::AbstractString; allow_not_found=true) -> Domain or nothing
get_domain(model::Model, domainid) -> Domain
```

Get Domain by `name` (may be nothing if `name` not matched) or `domainid` (range 1:num_domains).

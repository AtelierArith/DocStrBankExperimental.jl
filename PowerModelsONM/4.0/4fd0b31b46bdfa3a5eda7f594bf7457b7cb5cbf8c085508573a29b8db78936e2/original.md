```
write_json(
    file::String,
    data::Dict{String,<:Any};
    indent::Union{Int,Missing}=missing
)
```

Write JSON `data` to `file`. If `!ismissing(indent)`, JSON will be pretty-formatted with `indent`

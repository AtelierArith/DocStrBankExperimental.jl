```
write_json(
    file::String,
    data::Dict{String,<:Any};
    indent::Union{Int,Missing}=missing
)
```

JSON `data`を`file`に書き込みます。`indent`が`!ismissing(indent)`の場合、JSONは`indent`を使って整形されます。

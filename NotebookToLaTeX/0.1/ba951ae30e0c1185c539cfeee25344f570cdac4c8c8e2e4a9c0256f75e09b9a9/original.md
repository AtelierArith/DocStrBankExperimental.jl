```
nestedget(dict::Dict, keys::AbstractVector, default = nothing)
```

Checks whether `dict["key1"]["key2"]...["keyn"]` exists, returing it's value or the `default`.

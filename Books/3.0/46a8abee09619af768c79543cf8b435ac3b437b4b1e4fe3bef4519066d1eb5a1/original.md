```
Options(object;
    filename::Union{AbstractString,Nothing,Missing}=missing,
    caption::Union{AbstractString,Nothing,Missing}=missing,
    label::Union{AbstractString,Nothing,Missing}=missing)
```

Struct containing an `object` and some meta-information to be passed to the resulting document. The `caption` and `label` options are used by `pandoc-crossref`.

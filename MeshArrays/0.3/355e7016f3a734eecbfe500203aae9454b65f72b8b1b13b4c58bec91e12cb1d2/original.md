```
varmeta
```

varmeta data structure. By default, `unit` is `missing` (non-dimensional), `position` is `fill(0.5,3)` (cell center), time is `missing`, and `name` / `long_name` is `unknown`.

Available constructors:

```
varmeta(unit::Union{Unitful.Units,Number,Missing},position::Array{Float64,1},
        time::Union{DateTime,Missing,Array{DateTime,1}},name::String,long_name::String)
```

And:

`defaultmeta = varmeta(missing,fill(0.5,3),missing,"unknown","unknown")`

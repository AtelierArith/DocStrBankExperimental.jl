```
read_gmt(fn)
```

Read in a GMT file (MSigDB gene set format), where `fn` is the file path.

# Examples

```jldoctest
julia> res = read_gmt("h.all.v7.5.1.symbols.gmt")

julia> gn, gs = read_gmt("h.all.v7.5.1.symbols.gmt")

```

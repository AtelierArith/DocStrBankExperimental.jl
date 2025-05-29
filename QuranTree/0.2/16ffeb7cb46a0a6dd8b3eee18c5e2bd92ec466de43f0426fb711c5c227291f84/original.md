```
table(tnzl::TanzilRaw)
```

Convert the `TanzilRaw` read-only array into a tabularized `TanzilData` using `IndexedTable`.

# Examples

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> tnzldata = table(tnzl);
```

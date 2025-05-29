```
table(crps::CorpusRaw)
```

Convert the `CorpusRaw` read-only array into a tabularized `CorpusData` using `IndexedTable`.

# Examples

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data)
julia> crpsdata = table(crps);
```

```
load(data::QuranData)
```

Load the raw `QuranData` as a `ReadOnlyArray` for both Quranic Corpus and Tanzil Data.

# Examples

```julia-repl
julia> data = QuranData()
julia> crps, tnzl = load(data);
```

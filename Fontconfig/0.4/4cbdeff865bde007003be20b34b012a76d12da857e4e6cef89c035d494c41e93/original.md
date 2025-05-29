```
list(pat::Pattern=Pattern(), properties = ["family", "style", "file"])::Vector{Pattern}
```

Selects fonts matching `pat` and creates patterns from those fonts. These patterns containing only those  properties listed in `properties`, and returns a vector of unique such patterns, as a `Vector{Pattern}`.

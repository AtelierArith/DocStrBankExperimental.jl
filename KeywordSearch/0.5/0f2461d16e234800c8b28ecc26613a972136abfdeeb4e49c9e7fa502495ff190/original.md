```
match_all(query::AbstractQuery, corpus::Corpus)
```

Looks for all matches for `query` from all documents in `corpus`. Returns a `Vector` of `QueryMatch` objects corresponding to all of the matches found, across all doucments.

```
match_all(query::AbstractQuery, document::Document)
```

Looks for all matches for `query` in the document. Returns a `Vector` `QueryMatch` objects corresponding to all of the matches found.

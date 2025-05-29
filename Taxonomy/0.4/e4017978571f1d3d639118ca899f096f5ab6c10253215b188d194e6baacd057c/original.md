```
similarnames(query::AbstractString, db::Taxonomy.DB; distance::StringDistances.StringDistance=StringDistances.Levenshtein(), threshold::Float64=0.8)
similarnames(query::AbstractString; distance::StringDistances.StringDistance=StringDistances.Levenshtein(), threshold::Float64=0.8)
```

Find names similar to the `query` and return a `Vector` of `NamedTuple`s with taxid, name, and similarity. The similarities are calculated by the Lavenshtein distance by default. It can also be changed to other distances defined in `StringDistaces` package by specifying it in the distance argument. Omitting `db` automatically calls `current_db()`, which is usually the database that was last created.

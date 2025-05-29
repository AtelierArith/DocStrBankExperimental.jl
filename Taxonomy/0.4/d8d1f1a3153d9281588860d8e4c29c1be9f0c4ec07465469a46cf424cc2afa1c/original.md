```
name2taxids(name::AbstractString, db::Taxonomy.DB)
name2taxids(name::AbstractString)
```

Return a `Vector` of taxid from its `name`. `name` must match to the scientific name exactly. If multiple hits are found, return a multi-element `Vector`. If not, 1- or 0-element `Vector`.  Omitting `db` automatically calls `current_db()`, which is usually the database that was last created.

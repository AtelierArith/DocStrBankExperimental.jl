```
Taxon(taxid::Int, db::Taxonomy.DB)
Taxon(taxid::Int)
```

Construct a `Taxon` from its `taxid`. Omitting `db` automatically calls `current_db()`, which is usually the database that was last created.

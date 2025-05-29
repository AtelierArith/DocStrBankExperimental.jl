```
apply_schema(t, schema::StatsModels.Schema[, Mod::Type = Nothing])
```

Return a new term that is the result of applying `schema` to term `t` with destination model (type) `Mod`.  If `Mod` is omitted, `Nothing` will be used.

When `t` is a `ContinuousTerm` or `CategoricalTerm` already, the term will be returned unchanged *unless* a matching term is found in the schema.  This allows selective re-setting of a schema to change the contrast coding or levels of a categorical term, or to change a continuous term to categorical or vice versa.

When defining behavior for custom term types, it's best to dispatch on [`StatsModels.Schema`](@ref) for the second argument.  Leaving it as `::Any` will work in *most* cases, but cause method ambiguity in some.

```
extend(X::AbstractSheaf, cover::AbstractCover, sections::AbstractVector)
```

Extend a collection of sections to the unique section that restricts to the sections provided. The `sections` vector needs to be indexed in the same order as `enumerate(cover)`.

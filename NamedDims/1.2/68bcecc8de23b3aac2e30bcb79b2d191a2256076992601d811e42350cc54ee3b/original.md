```
rename(nda::NamedDimsArray, names)
rename(nda::NamedDimsArray, pairs)
```

Returns a new `NamedDimsArray` with the given dimension `names` or `pairs` of `old=>new` names. `rename` outright replaces the names; while still wrapping the same backing array. Unlike the constructor, it does not require that new names are compatible with the old names (though you do still need to match the number of dimensions).

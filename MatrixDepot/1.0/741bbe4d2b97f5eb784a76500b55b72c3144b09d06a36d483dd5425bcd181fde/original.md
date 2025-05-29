```
keyword(word::Union{AbstractString,Tuple,Vector})
```

Predicate function checks, if `word` is contained in on to the textual metadata fields `[:notes, :title, :kind, :author]`. Tuples and Vectors are interpreted as `AND` resp. `OR`.

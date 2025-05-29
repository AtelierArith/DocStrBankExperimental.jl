```
invert(text, ops::Vector{Range}) -> Vector{Range}
```

Given a set of edits on a text, produce the inverse set of edits.

```julia
Pinot.apply(Pinot.apply(text, edits), Pinot.inverse(edits)) == text
```

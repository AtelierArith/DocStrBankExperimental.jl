```
allcompletions(r::ReplCmd)
```

Obtain all possible `String` completion candidates for `r`. This defaults to the empty vector `String[]`.

`allcompletions` is only called when `completions(r, sofar::AbstractString)` is not implemented.

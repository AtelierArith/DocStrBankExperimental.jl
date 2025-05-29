```
FuzzyQuery(text, dist, threshold; replacements=AUTOMATIC_REPLACEMENTS) <: AbstractQuery
```

A query to search for an fuzzy match of a string, with three fields:

  * `text::String`: the text to match
  * `dist::D`: the distance measure to use; defaults to `DamerauLevenshtein()`
  * `threshold::T`: the maximum threshold allowed for a match; defaults to 2.

The `text` is automatically processed by applying the replacements `replacements` (which defaults to [`AUTOMATIC_REPLACEMENTS`](@ref)).

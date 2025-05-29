```
augment(term) -> Vector{String}
```

Given a term, returns a list of terms which should be treated as synonyms. Currently only supports agumenting (spaces or hyphens) with (spaces, no spaces).

## Example

```jldoctest
julia> KeywordSearch.augment("arctic wolf")
2-element Vector{String}:
 "arctic wolf"
 "arcticwolf"
 
```

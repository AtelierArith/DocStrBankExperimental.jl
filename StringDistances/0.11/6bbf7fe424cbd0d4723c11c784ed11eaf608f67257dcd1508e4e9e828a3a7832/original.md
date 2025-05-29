TokenSet(dist)

Creates the `TokenSet{dist}` distance, which is only defined on AbstractStrings.

`TokenSet{dist}` returns the minimum the distances between: [SORTED*INTERSECTION] [SORTED*INTERSECTION] + [SORTED*REST*OF*STRING1] [SORTED*INTERSECTION] + [SORTED*REST*OF_STRING2] See: http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/

### Examples

```julia-repl
julia> s1 = "New York Mets vs Atlanta"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> TokenSet(RatcliffObershelp())(s1, s2)
0.0
```

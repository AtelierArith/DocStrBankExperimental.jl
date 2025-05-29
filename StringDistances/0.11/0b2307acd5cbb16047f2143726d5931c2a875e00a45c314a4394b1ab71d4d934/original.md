TokenSort(dist)

Creates the `TokenSort{dist}` distance.

`TokenSort{dist}` returns the distance between strings after reording words alphabetically. See http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/

It is only defined on AbstractStrings.

### Examples

```julia-repl
julia> s1 = "New York Mets vs Atlanta Braves"
julia> s1 = "New York Mets vs Atlanta Braves"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> TokenSort(RatcliffObershelp())(s1, s2)
0.0
```

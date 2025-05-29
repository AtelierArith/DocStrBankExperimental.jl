Partial(dist)

Creates the `Partial{dist}` distance.

`Partial{dist}`  returns the  minimum distance  between the shorter string and substrings of the longer string that have a length equal to the shorter string.

See http://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/

### Examples

```julia-repl
julia> s1 = "New York Mets vs Atlanta Braves"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> Partial(RatcliffObershelp())(s1, s2)
0.5483870967741935
```

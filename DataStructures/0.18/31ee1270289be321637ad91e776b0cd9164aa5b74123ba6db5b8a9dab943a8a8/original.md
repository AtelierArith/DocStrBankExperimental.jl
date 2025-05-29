```
 nlargest(acc::Accumulator, [n])
```

Returns a sorted vector of the `n` most common elements, with their counts. If `n` is omitted, the full sorted collection is returned.

This corresponds to Python's `Counter.most_common` function.

Example

```
julia> nlargest(counter("abbbccddddda"))

4-element Array{Pair{Char,Int64},1}:
 'd'=>5
 'b'=>3
 'c'=>2
 'a'=>2


julia> nlargest(counter("abbbccddddda"),2)

2-element Array{Pair{Char,Int64},1}:
 'd'=>5
 'b'=>3

```

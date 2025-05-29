`arrangements(mset[,k])`, `narrangements(mset[,k])`

`arrangements`  returns  the  arrangements  of  the  multiset `mset` (a not necessarily  sorted  collection  with  possible  repetitions).  If a second argument   `k`  is  given,  it  returns  arrangements  with  `k`  elements. `narrangements` returns (faster) the number of arrangements.

An *arrangement* of `mset` with `k` elements is a subsequence of length `k` taken in arbitrary order, representated as a `Vector`. When `k==length(mset)` it is also called a permutation.

As  an example of arrangements  of a multiset, think  of the game Scrabble. Suppose  you have the six  characters of the word  'settle' and you have to make a two letter word. Then the possibilities are given by

```julia-repl
julia> narrangements("settle",2)
14
```

while all possible words (including the empty one) are:

```julia-repl
julia> narrangements("settle")
523
```

The  result returned  by 'arrangements'  is sorted  (the elements of `mset` must  be sortable), which means in  this example that the possibilities are listed  in the same  order as they  appear in the  dictionary. Here are the two-letter words:

```julia-repl
julia> String.(arrangements("settle",2))
14-element Vector{String}:
 "ee"
 "el"
 "es"
 "et"
 "le"
 "ls"
 "lt"
 "se"
 "sl"
 "st"
 "te"
 "tl"
 "ts"
 "tt"
```

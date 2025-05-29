```
NGramIterator{T}
```

Iterates over ngram codes of collection of integers `s` using [`Mill.string_start_code()`](@ref) and [`Mill.string_end_code()`](@ref) for padding. NGram codes are computed as in positional number systems, where items of `s` are digits, `b` is the base, and `m` is modulo.

In order to reduce collisions when mixing ngrams of different order one should avoid zeros and negative integers in `s` and should set base `b` to the expected number of unique tokens in `s`.

See also: [`NGramMatrix`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref).

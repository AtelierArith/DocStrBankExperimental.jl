```
NGramMatrix{T, U, V} <: AbstractMatrix{U}
```

A matrix-like structure for lazily representing sequences like strings as ngrams of cardinality `n` using `b` as a base for calculations and `m` as the modulo. Therefore, the matrix has `m` rows and one column for representing each sequence. Missing sequences are supported.

See also: [`NGramIterator`](@ref), [`ngrams`](@ref), [`ngrams!`](@ref), [`countngrams`](@ref),     [`countngrams!`](@ref).

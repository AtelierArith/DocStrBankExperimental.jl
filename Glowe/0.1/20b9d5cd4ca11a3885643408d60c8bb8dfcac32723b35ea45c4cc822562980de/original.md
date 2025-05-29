```
cooccur(corpus, vocab, cooccurrences; verbose=2, symmetric=0, window_size=15, memory=4.0, max_product=nothing, overflow_length=nothing, overflow_file="overflow", distance_weighting=1)
```

Calculates word-word cooccurrence statistics.

# Arguments

  * `corpus::AbstractString` input corpus file path
  * `vocab::AbstractString` input vocabulary file path (the vocabulary contains truncated unigram counts, produced by `vocab_count`)
  * `cooccurrences::AbstractString` output cooccurrences file path

# Keyword arguments

  * `verbose::Int` set verbosity: 0, 1, 2 (default) or 3
  * `symmetric::Int` if <int> = 0, only use left context; if <int> = 1 (default), use left and right
  * `window_size::Int` number of context words to the left (and to the right, if symmetric = 1); default 15
  * `memory::Float64` soft limit for memory consumption, in GB – based on simple heuristic, so not extremely accurate; default 4.0
  * `max_product::Union{Nothing, Int}` limit the size of dense cooccurrence array by specifying the max product <int> of the frequency counts of the two cooccurring words. This value overrides that which is automatically produced by `memory`. Typically only needs adjustment for use with very large corpora
  * `overflow_length::Union{Nothing, Int}` limit to length <int> the sparse overflow array, which buffers cooccurrence data that does not fit in the dense array, before writing to disk. This value overrides that which is automatically produced by `memory`. Typically only needs adjustment for use with very large corpora
  * `overflow_file::String` filename, excluding extension, for temporary files; default "overflow"
  * `distance_weighting::Int` if <int> = 0, do not weight cooccurrence count by distance between words; if <int> = 1 (default), weight the cooccurrence count by inverse of distance between words"

# Examples

```
# It is assumed that vocab.txt exists and has been created by `vocab_count`
julia> cooccur("corpus.txt", "vocab.txt", "cooccurrences.bin", verbose=2, symmetric=0, window_size=10, memory=8.0, overflow_file="tempoverflow")
```

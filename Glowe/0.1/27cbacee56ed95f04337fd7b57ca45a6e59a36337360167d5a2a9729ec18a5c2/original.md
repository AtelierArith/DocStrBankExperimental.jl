```
shuffle(cooccurences, shuffled; verbose=2, memory=4.0, array_size=nothing, temp_file="temp_shuffle")
```

Shuffles entries of word-word cooccurrence files.

# Arguments

  * `cooccurences::AbstractString` input cooccurrences file path
  * `shuffled::AbstractString` output shuffled cooccurences file path

# Keyword arguments

  * `verbose::Int` set verbosity: 0, 1, or 2 (default)
  * `memory::Float64` soft limit for memory consumption, in GB; default 4.0
  * `array_size::Union{Nothing, Int}` limit to length <int> the buffer which stores chunks of data to shuffle before writing to disk. This value overrides that which is automatically produced by `memory`
  * `temp_file`::String filename, excluding extension, for temporary files; default "temp_shuffle"

# Examples

```
# It is assumed that cooccurences.bin exists and has been created by `cooccur`
julia> shuffle("cooccurences.bin", "shuffled.bin", verbose=2, memory=8.0)
```

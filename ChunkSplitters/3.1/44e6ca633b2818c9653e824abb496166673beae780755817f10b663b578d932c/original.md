```
index_chunks(collection;
    n::Union{Nothing, Integer}=nothing,
    size::Union{Nothing, Integer}=nothing,
    [split::Split=Consecutive(),]
    [minsize::Union{Nothing,Integer}=nothing,]
)
```

Returns an iterator that splits the *indices* of `collection` into `n`-many chunks (if `n` is given) or into chunks of a certain size (if `size` is given). The returned iterator can be used to process chunks of *indices* of `collection` one after another. If you want to process chunks of *elements* of `collection`, check out `chunks(...)` instead.

The keyword arguments `n` and `size` are mutually exclusive.

### Keyword arguments (optional)

  * `split` can be used to determine the splitting strategy, i.e. the distribution of the indices among chunks. If `split = Consecutive()` (default), chunks will hold consecutive indices and will hold approximately the same number of indices (as far as possible). If `split = RoundRobin()`, indices will be assigned to chunks in a round-robin fashion.
  * `minsize` can be used to specify the minimum size of a chunk, and can be used in combination with the `n` keyword. If, for the given `n`, the chunks are smaller than `minsize`, the number of chunks will be decreased to ensure that each chunk is at least `minsize` long. By default, `minsize == 1` when the keyword is set to `nothing`. If `minsize` is greater than the length of the collection, there will be only one chunk.

### Noteworthy

If you need a running chunk index you can combine `chunks` with `enumerate`. In particular, `enumerate(index_chunks(...))` can be used in conjuction with `@threads`.

### Requirements

The type of the input `collection` must have at least `firstindex`, `lastindex`, and `length` functions defined, as well as `ChunkSplitters.is_chunkable(::typeof(collection)) = true`. Out of the box, `AbstractArray`s and `Tuple`s are supported.

## Examples

```jldoctest
julia> using ChunkSplitters

julia> x = rand(7);

julia> collect(index_chunks(x; n=3))
3-element Vector{UnitRange{Int64}}:
 1:3
 4:5
 6:7

julia> collect(enumerate(index_chunks(x; n=3)))
3-element Vector{Tuple{Int64, UnitRange{Int64}}}:
 (1, 1:3)
 (2, 4:5)
 (3, 6:7)

julia> collect(index_chunks(1:7; size=3))
3-element Vector{UnitRange{Int64}}:
 1:3
 4:6
 7:7
```

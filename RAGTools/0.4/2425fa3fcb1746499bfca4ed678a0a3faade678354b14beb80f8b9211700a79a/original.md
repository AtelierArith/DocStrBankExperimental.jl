```
SubChunkIndex
```

A view of the parent index with respect to the `chunks` (and chunk-aligned fields).  All methods and accessors working for `AbstractChunkIndex` also work for `SubChunkIndex`. It does not yet work for `MultiIndex`.

# Fields

  * `parent::AbstractChunkIndex`: the parent index from which the chunks are drawn    (always the original index, never a view)
  * `positions::Vector{Int}`: the positions of the chunks in the parent index (always    refers to original PARENT index, even if we create a view of the view)

# Example

```julia
cc = CandidateChunks(index.id, 1:10)
sub_index = @view(index[cc])
```

You can use `SubChunkIndex` to access chunks or sources (and other fields) from a parent index, eg,

```julia
RT.chunks(sub_index)
RT.sources(sub_index)
RT.chunkdata(sub_index) # slice of embeddings
RT.embeddings(sub_index) # slice of embeddings
RT.tags(sub_index) # slice of tags
RT.tags_vocab(sub_index) # unchanged, identical to parent version
RT.extras(sub_index) # slice of extras
```

Access the parent index that the `positions` correspond to

```julia
parent(sub_index)
RT.positions(sub_index)
```

```
ParsedPayload{B, C<:AbstractParsingContext}
```

A payload of parsed results, which is passed to `consume!` after each `populate_result_buffer!` call.

# Fields:

  * `row_num::Int`: row number of the first row in the payload
  * `len::Int`: number of rows in the payload
  * `results::B`: parsed result buffer which was populated by `populate_result_buffer!`
  * `parsing_ctx::C`: library-provided data (to distinguish JSONL and CSV processing)
  * `chunking_ctx::ChunkingContext`: contains the raw bytes, synchronization objects and newline positions
  * `eols_buffer_index::Int32`: The start index of the newline positions in `chunking_ctx.newline_positions` that this payload corresponds to.

# See also:

  * [`consume!`](@ref), [`AbstractParsingContext`](@ref), [`ChunkingContext`](@ref), [`AbstractResultBuffer`](@ref), [`PayloadOrderer`](@ref)

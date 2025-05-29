```
ChunkingContext(
    buffersize::Integer,
    nworkers::Integer,
    limit::Integer,
    comment::Union{Nothing,UInt8,String,Char,Vector{UInt8}}
) -> ChunkingContext
```

A context object used to coordinate parallel parsing of a single file, chunk by chunk.

The user can use this object to specify the size of the byte buffer(s) to allocate, the number of worker tasks to spawn and the maximum number of rows to parse in `parse_file_parallel`.

# Arguments:

  * `buffersize`: the size of the byte buffer to allocate .   If the input is bigger than `buffersize`, a secondary `ChunkingContext` object will be used to   double-buffer the input, which will allocate a new buffer of the same size as `buffersize`.
  * `nworkers`: the number of worker tasks that should be spawned in `parse_file_parallel`.
  * `limit`: the maximum number of rows to parse, see `limit_eols!`, by default no limit is set.
  * `comment`: the comment prefix to skip, if any. By default no comment prefix is skipped.

# Notes:

  * One can use the `id` and `buffer_refills` fields to uniquely identify a chunk of input.

The `id` field is necessary because we internally create a secondary `ChunkingContext` object, with `id` equal to the `id` of the original `ChunkingContext` + 1.

  * The `counter` field is used to synchronize the parser/consumer tasks.
  * The `newline_positions` field is used to store the newline positions in the input.
  * The `bytes` field is used to store the raw bytes ingested from the input.
  * `comment` can be used to skip the *initial* comment lines in the `skip_rows_init!`. This value is also passed to `populate_result_buffer!` for user to apply handle commented rows in the middle of the file during parsing (`_startswith` could be used to do the check).
  * The `buffersize` should be large enough to fit the longest row in the input, otherwise the lexer will fail.
  * The `buffersize` should be chosen such that each of the `nworkers` tasks has enough bytes to work on. Using 1MiB per task seems to work reasonably well in practice.

# See also:

  * [`parse_file_parallel`](@ref), [`parse_file_serial`](@ref)

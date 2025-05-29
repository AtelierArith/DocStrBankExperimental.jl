```
parse_file_parallel(
    lexer::Lexer,
    parsing_ctx::AbstractParsingContext,
    consume_ctx::AbstractConsumeContext,
    chunking_ctx::ChunkingContext,
    result_buffers::Vector{<:AbstractResultBuffer},
    ::Type{CT}=Tuple{}
) where {CT} -> Nothing
```

Parse the file in `lexer.io` in parallel using `chunking_ctx.nworkers` tasks. User must provide a `populate_result_buffer!` method which is used to parse ingested data in `chunking_ctx.bytes`, using the newline positions in `chunking_ctx.newline_positions` as row boundaries into the `result_buffers`. The `consume!` method is called after each `populate_result_buffer!` call, so the user can process the parsed results in parallel. No `result_buffer` is accessed by more than one task at a time.

# Arguments:

  * `lexer`: a `NewlineLexers.Lexer` object which is used to find newline positions in the input. The

type of the lexer affects whether the search is quote-aware or not.

  * `parsing_ctx`: a user-provided object which is passed to `populate_result_buffer!`
  * `consume_ctx`: a user-provided object which is passed to `consume!`
  * `chunking_ctx`: an internal object that is used to keep track of the current chunk of data being processed
  * `result_buffers`: a vector of user-provided objects which are used to store the parsed results
  * `CT`: an optional, compile-time known type which is passed to `populate_result_buffer!`.

This is bit of niche functionality required by ChunkedCSV, which needs to know about "custom types" at compile time in order to unroll the parsing loop on them.

# Exceptions:

  * `UnmatchedQuoteError`: if the input ends with an unmatched quote
  * `NoValidRowsInBufferError`: if not a single newline was found in the input buffer
  * `CapturedException`: if an exception was thrown in one of the parser/consumer tasks

# Notes:

  * You can initialize the `chunking_ctx` yourself using `read_and_lex!` or with `initial_read!` + `initial_lex!`

which gives you the opportunity to sniff the first chunk of data before you call `parse_file_parallel`.

  * If the input is bigger than `chunking_ctx.bytes`, a secondary `chunking_ctx` object will be used to

double-buffer the input, which will allocate a new buffer of the same size as `chunking_ctx.bytes`.

  * This function spawns `chunking_ctx.nworkers` + 1 tasks.

See also [`populate_result_buffer!`](@ref), [`consume!`](@ref), [`parse_file_serial`](@ref).

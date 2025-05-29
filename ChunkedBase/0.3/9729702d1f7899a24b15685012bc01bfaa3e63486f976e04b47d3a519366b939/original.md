```
parse_file_serial(
    lexer::Lexer,
    parsing_ctx::AbstractParsingContext,
    consume_ctx::AbstractConsumeContext,
    chunking_ctx::ChunkingContext,
    result_buf::AbstractResultBuffer,
    ::Type{CT}=Tuple{},
) where {CT}
```

The serial analog of `parse_file_parallel` which doesn't spawn any tasks, useful for debugging and processing very small files.

See also [`populate_result_buffer!`](@ref), [`consume!`](@ref), [`parse_file_parallel`](@ref).

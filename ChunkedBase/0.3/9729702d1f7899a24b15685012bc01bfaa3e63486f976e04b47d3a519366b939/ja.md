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

タスクを生成しない `parse_file_parallel` のシリアルアナログで、デバッグや非常に小さなファイルの処理に便利です。

関連情報としては、[`populate_result_buffer!`](@ref)、[`consume!`](@ref)、[`parse_file_parallel`](@ref)があります。

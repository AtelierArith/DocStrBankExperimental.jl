```
PayloadOrderer{B, C<:AbstractParsingContext} <: AbstractChannel{ParsedPayload{B,C}}
```

ペイロードが順番に消費されることを保証するチャネルのようなオブジェクトです。

`PayloadOrderer`を使用するには、独自の`AbstractConsumeContext`を作成し、それを含めて`consume!`をオーバーライドして、`PayloadOrderer`にペイロードを`put!`し、別のタスクを使用してそれからペイロードを`take!`する必要があります。例えば：

```
struct MyConsumeContext <: AbstractConsumeContext
    orderer::PayloadOrderer{MyResultBuffer, MyParsingContext}
end

# ランダムな順序で到着するペイロードをオーダラーに転送します
function ChunkedBase.consume!(consume_ctx::MyConsumeContext, payload::ParsedPayload)
    put!(consume_ctx.orderer, payload)
end

# ペイロードごとに`ChunkedBase.task_done!`が2回呼び出されることを期待します。
# デフォルトでは、`consume!`の後に1回呼び出しますが、
# オーダラーから取得するタスクで別の1回を追加します。
# これにより、現在のチャンクがタスクが完了した後に再利用されないことが保証されます。
function ChunkedBase.setup_tasks!(::MyConsumeContext, chunking_ctx::ChunkingContext, ntasks::Int)
    set!(chunking_ctx.counter, 2*ntasks)
end

consume_ctx = MyConsumeContext(PayloadOrderer{MyResultBuffer, MyParsingContext}())

# ペイロードを順番に処理する必要があるタスク
@spawn begin
    while true
        payload = take!(consume_ctx.orderer)
        do_something_that_requires_ordered_results(payload)
        task_done!(consume_ctx, payload.chunking_ctx)
    end
end

parse_file_parallel(lexer, parsing_ctx, consume_ctx, chunking_ctx, result_buf)
```

注意：`PayloadOrderer`の`take!`を複数のタスクから呼び出すことは安全ではありません。

# 参照：

  * [`ParsedPayload`](@ref)

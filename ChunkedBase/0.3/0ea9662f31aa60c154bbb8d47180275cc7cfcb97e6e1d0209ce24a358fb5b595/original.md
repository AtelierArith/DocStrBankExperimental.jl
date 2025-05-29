```
PayloadOrderer{B, C<:AbstractParsingContext} <: AbstractChannel{ParsedPayload{B,C}}
```

A channel-like object that ensures that the payloads are consumed in order.

To use the `PayloadOrderer` you should create your own `AbstractConsumeContext` that contains it and override the `consume!` to only `put!` payloads in the `PayloadOrderer` and `take!` payloads from it using a separate task. For example:

```
struct MyConsumeContext <: AbstractConsumeContext
    orderer::PayloadOrderer{MyResultBuffer, MyParsingContext}
end

# Forward the payloads, which will arrive in random order, to the orderer
function ChunkedBase.consume!(consume_ctx::MyConsumeContext, payload::ParsedPayload)
    put!(consume_ctx.orderer, payload)
end

# Expect `ChunkedBase.task_done!` to be called twice per payload.
# By default, we'd do it once after every `consume!`
# But we'll add another one in the task that takes from the orderer.
# This will make sure that the current chunk won't ger recycled after our task is done with it.
function ChunkedBase.setup_tasks!(::MyConsumeContext, chunking_ctx::ChunkingContext, ntasks::Int)
    set!(chunking_ctx.counter, 2*ntasks)
end

consume_ctx = MyConsumeContext(PayloadOrderer{MyResultBuffer, MyParsingContext}())

# Our task that needs to process the payloads in order
@spawn begin
    while true
        payload = take!(consume_ctx.orderer)
        do_something_that_requires_ordered_results(payload)
        task_done!(consume_ctx, payload.chunking_ctx)
    end
end

parse_file_parallel(lexer, parsing_ctx, consume_ctx, chunking_ctx, result_buf)
```

NOTE: It is not safe to call `take!` from multiple tasks on a `PayloadOrderer`.

# See also:

  * [`ParsedPayload`](@ref)

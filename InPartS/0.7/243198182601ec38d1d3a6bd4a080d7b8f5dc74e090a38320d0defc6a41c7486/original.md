```
BinaryDumpCallback(trigger::AbstractCallback, filename)
```

Callback that uses the Julia serializer to dump the [`DynamicState`](@ref) into a binary output file at `filename`. Intermediate files are written in [`prepropagate!`](@ref) whenever the `trigger` callback is triggered, a final file is written on [`finalize!`](@ref) or [`freeze!`](@ref)

Not intended for long-term storage of data (use [`SaveCallback`](@ref) instead).

```
setup_tasks!(consume_ctx::AbstractConsumeContext, chunking_ctx::ChunkingContext, ntasks::Int)
```

Set the number of units of work that the parser/consume tasks need to finish (and report back as done via e.g. `task_done!`) before the current chunk of input data is considered to be entirely processed.

This function is called just after the we're done detecting newline positions in the current chunk of data and we are about to submit partitions of the detected newlines to the parse/consume tasks.

`ntasks` is between 1 and `nworkers` argument to `parse_file`, depending on the size of the input. Most of the time, the value is `nworkers` is used, but for smaller buffer sizes, smaller files or when handling the last bytes of the file, `ntasks` will be smaller as we try to ensure the minimal average tasks size if terms of bytes of input is at least 16.000 KiB. For `:serial` parsing mode, `ntasks` is always 1.

You should override this method when you further subdivide the amount of concurrent work on the chunk, e.g. when you want to process each column separately in `@spawn` tasks, in which case you'd expect there to be `ntasks * (1 + length(parsing_ctx.schema))` units of work per chunk (in which case you'd have to manually call `task_done!` in the column-processing tasks).

See also [`consume!`](@ref), [`setup_tasks!`](@ref), [`task_done!`](@ref), [`cleanup`](@ref)

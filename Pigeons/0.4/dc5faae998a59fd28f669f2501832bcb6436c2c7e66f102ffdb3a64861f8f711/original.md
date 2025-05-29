Save the full trace for the target chain to disk. 

The `disk` recorders are safe to use in a multi-threaded and/or  distributed context as each replica uses its own file.

To post-process files in the correct order, use [`process_sample`](@ref).

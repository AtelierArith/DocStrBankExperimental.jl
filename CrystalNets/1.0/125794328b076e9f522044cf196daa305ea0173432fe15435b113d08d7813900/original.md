```
add_to_current_archive!(id, genome)
```

Mark `genome` as the topological genome associated with the name `id` in the current archive.

The input `id` and `genome` are not modified by this operation.

!!! note
    This modification will only last for the duration of this Julia session.

    If you wish to save the archive and use it for subsequent runs, use [`set_default_archive!`](@ref) after calling this function.


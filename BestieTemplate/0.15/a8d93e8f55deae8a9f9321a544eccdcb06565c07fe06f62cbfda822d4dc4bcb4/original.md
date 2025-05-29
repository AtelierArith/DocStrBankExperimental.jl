```
update([data]; kwargs...)
update(dst_path[, data]; kwargs...)
```

Run the update command of copier, updating the `dst_path` (or the current path if omitted) with a new version of the template with a new version of the template.

The `data` argument is a dictionary of answers (values) to questions (keys) that can be used to bypass some of the interactive questions.

## Keyword arguments

The keyword arguments are passed directly to the internal [`Copier.update`](@ref).

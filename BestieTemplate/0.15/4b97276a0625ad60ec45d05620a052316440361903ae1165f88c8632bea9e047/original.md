```
generate(dst_path[, data]; kwargs...)
generate(src_path, dst_path[, data]; true, kwargs...)
```

Generates a new project at the path `dst_path` using the template. If the `dst_path` already exists, this will throw an error, unless `dst_path = "."`. For existing packages, use `BestieTemplate.apply` instead.

Runs the `copy` command of [copier](https://github.com/copier-org/copier) with the BestieTemplate template. If `src_path` is not informed, the GitHub URL of BestieTemplate.jl is used.

The `data` argument is a dictionary of answers (values) to questions (keys) that can be used to bypass some of the interactive questions.

## Keyword arguments

  * `warn_existing_pkg::Boolean = true`: Whether to check if you actually meant `update`. If you run `generate` and the `dst_path` contains a `.copier-answers.yml`, it means that the copy was already made, so you might have means `update` instead. When `true`, a warning is shown and execution is stopped.
  * `quiet::Boolean = false`: Whether to print greetings, info, and other messages. This keyword is also used by copier.

The other keyword arguments are passed directly to the internal [`Copier.copy`](@ref).

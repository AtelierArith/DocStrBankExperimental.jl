```
apply(dst_path[, data]; kwargs...)
apply(src_path, dst_path[, data]; true, kwargs...)
```

Applies the template to an existing project at path $dst_path$. If the `dst_path` does not exist, this will throw an error. For new packages, use `BestieTemplate.generate` instead.

Runs the `copy` command of [copier](https://github.com/copier-org/copier) with the BestieTemplate template. If `src_path` is not informed, the GitHub URL of BestieTemplate.jl is used.

The `data` argument is a dictionary of answers (values) to questions (keys) that can be used to bypass some of the interactive questions.

## Keyword arguments

  * `guess:Bool = true`: Whether to try to guess some of the data from the package itself.
  * `warn_existing_pkg::Bool = true`: Whether to check if you actually meant `update`. If you run `apply` and the `dst_path` contains a `.copier-answers.yml`, it means that the copy was already made, so you might have means `update` instead. When `true`, a warning is shown and execution is stopped.
  * `quiet::Bool = false`: Whether to print greetings, info, and other messages. This keyword is also used by copier.

The other keyword arguments are passed directly to the internal [`Copier.copy`](@ref).

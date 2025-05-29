```
watch_file(file::AbstractString; jetconfigs...)
```

Watches `file` and keeps re-triggering analysis with [`report_file`](@ref) on code update. JET will try to analyze all the `include`d files reachable from `file`, and it will re-trigger analysis if there is code update detected in any of the `include`d files.

This entry point currently uses [Revise.jl](https://timholy.github.io/Revise.jl/stable/) to monitor code updates, and *can only be used after Revise has been loaded into the session*. So note that you'll need to have run e.g., `using Revise` at some earlier stage to use it. Revise offers possibilities to track changes in files that are not directly analyzed by JET, including changes made to `Base` files using configurations like `revise_modules = [Base]`. See [watch configurations](@ref watch-config) for more details.

!!! warning
    This interface is very experimental and likely to subject to change or removal without notice.


See also [`report_file`](@ref).

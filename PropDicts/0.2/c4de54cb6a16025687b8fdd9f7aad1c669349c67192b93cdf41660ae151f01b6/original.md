```
readprops(filename::AbstractString; subst_pathvar::Bool = true, subst_env::Bool = true, trim_null::Bool = true)
readprops(filenames::Vector{<:AbstractString}; ...)
```

Read a [`PropDict`](@ref) from a single or multiple JSON files.

If multiple files are given, they are merged into a single `PropDict` using `merge`.

`subst_pathvar` controls whether `$_` should be substituted with the directory path of the/each JSON file within string values (but not field names).

`subst_env` controls whether `$ENVVAR` should be substituted with the value of the each environment variable `ENVVAR` within string values (but not field names).

`trim_null` controls whether JSON `null` values should be removed entirely.

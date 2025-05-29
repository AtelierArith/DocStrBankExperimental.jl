```
set_preamble()
set_preamble(::TypstString)
```

Use Preferences.jl such that after restarting Julia, the [`preamble`](@ref) is initialized to the given [`TypstString`](@ref).

If the `TypstString` is not provided, reset the `preamble` to it's default value.

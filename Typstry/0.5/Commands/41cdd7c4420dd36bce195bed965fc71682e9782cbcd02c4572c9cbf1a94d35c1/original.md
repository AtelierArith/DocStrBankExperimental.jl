```
typst(::AbstractString; catch_interrupt = true, ignorestatus = true)
```

Convenience function intended for interactive use, emulating the typst command line interface. Be aware, however, that it strictly splits on spaces and does not provide any shell-style escape mechanism, so it will not work if there are, e.g., filenames with spaces.

When `catch_interrupt` is true, CTRL-C quietly quits the command. When [`ignorestatus`](@ref) is true, a Typst failure will not imply a julia error.

If the `"TYPST_FONT_PATHS"` environment variable is not set, it is temporarily set to [`julia_mono`](@ref).

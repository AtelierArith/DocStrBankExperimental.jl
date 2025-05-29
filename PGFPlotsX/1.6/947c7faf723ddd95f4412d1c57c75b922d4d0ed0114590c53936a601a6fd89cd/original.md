```
TikzDocument(elements...; use_default_preamble = true, preamble = [])
```

Corresponds to a LaTeX document, usually wrapping `TikzPicture`s.

`use_default_preamble` determines whether a preamble is added from the global variables (see [`CUSTOM_PREAMBLE`](@ref) and [`CUSTOM_PREAMBLE_PATH`](@ref)).

`preamble` is appended after the default one (if any).

`push!` can be used to append elements after construction, and similarly `push_preamble!` for the preamble.

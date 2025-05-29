```
Sort(col₁, col₂, ..., colₙ; kwargs...)
Sort([col₁, col₂, ..., colₙ]; kwargs...)
Sort((col₁, col₂, ..., colₙ); kwargs...)
```

Sort the rows of selected columns `col₁`, `col₂`, ..., `colₙ` by forwarding the `kwargs` to the `sortperm` function.

```
Sort(regex; kwargs...)
```

Sort the rows of columns that match with `regex`.

# Examples

```julia
Sort(:a)
Sort(:a, :c, rev=true)
Sort([1, 3, 5], by=row -> abs.(row))
Sort(("a", "c", "e"))
Sort(r"[ace]")
```

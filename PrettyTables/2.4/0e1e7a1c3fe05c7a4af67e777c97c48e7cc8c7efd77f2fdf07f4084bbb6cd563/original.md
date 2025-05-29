```
struct Highlighter
```

Defines the default highlighter of a table when using the text backend.

# Fields

  * `f::Function`: Function with the signature `f(data, i, j)` in which should return `true`   if the element `(i,j)` in `data` must be highlighter, or `false` otherwise.
  * `fd::Function`: Function with the signature `f(h, data, i, j)` in which `h` is the   highlighter. This function must return the `Crayon` to be applied to the cell that must   be highlighted.
  * `crayon::Crayon`: The `Crayon` to be applied to the highlighted cell if the default `fd`   is used.

# Remarks

This structure can be constructed using three helpers:

```
Highlighter(f::Function; kwargs...)
```

where it will construct a `Crayon` using the keywords in `kwargs` and apply it to the highlighted cell,

```
Highlighter(f::Function, crayon::Crayon)
```

where it will apply the `crayon` to the highlighted cell, and

```
Highlighter(f::Function, fd::Function)
```

where it will apply the `Crayon` returned by the function `fd` to the highlighted cell.

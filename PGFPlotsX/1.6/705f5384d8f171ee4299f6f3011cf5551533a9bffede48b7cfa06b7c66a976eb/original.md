```
@pgf { ... }

@pgf some(nested(form({ ... })),
          with_multiple_options({ ... }))
```

Construct [`Options`](@ref) from comma-delimited `key` (without value), `key = value`, `key : value`, or `key => value` pairs enclosed in `{ ... }`, anywhere in the expression.

Keys can be

1. symbols, which are converted to strings, with `_` replaced by spaces,
2. strings or raw strings, used as is

The argument is traversed recursively, allowing `{ ... }` expressions in multiple places.

Multi-word keys need to be either quoted, or written as strings with underscores.

```julia
@pgf {
    "only marks",
    mark_size = "0.6pt",
    mark = "o",
    color => "black",
}
```

Another `Options` can be spliced into one being created using `...`, e.g.

```
theme = @pgf {xmajorgrids, x_grid_style = "white"}

axis_opt = @pgf {theme..., title = "My figure"}
```

Use `{}` for empty options that print as `[]` in LaTeX.

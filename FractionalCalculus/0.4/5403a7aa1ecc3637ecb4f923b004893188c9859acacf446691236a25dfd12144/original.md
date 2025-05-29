# Grünwald–Letnikov sense fractional dervivative.

```
fracdiff(f, α, start_point, end_point, GLDirect())
```

### Example:

```julia-repl
julia> fracdiff(x->x^5, 0, 0.5, GLDirect())
```

!!! info "Scope"
    Please note Grunwald-Letnikov sense fracdiff only support $0 < \alpha < 1$.


Please refer to [Grünwald–Letnikov derivative](https://en.wikipedia.org/wiki/Gr%C3%BCnwald%E2%80%93Letnikov_derivative) for more details.

Grunwald Letnikov direct compute method to obtain fractional derivative, precision are guaranteed but cause more memory allocation and compilation time.

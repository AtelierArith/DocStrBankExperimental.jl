```
function column(args...; size=-1, xs=-1, sm=-1, md=-1, lg=-1, xl=-1, kwargs...)
```

Creates a `div` HTML element with Quasar's Flexgrid CSS class `column`. Such columns typically contain elements created with [`cell`](@ref), [`row`](@ref), `column`, or other elements that manually receive grid classes, e.g. `"col"`, `"col-sm-5"`.

The grid size kwargs `size`, `xs`, etc. are explained in more detail in the docs of [`cell`](@ref).

### Example

```julia
julia> column(span("Hello"))
"<div class="column"><span>Hello</span></div>"
```

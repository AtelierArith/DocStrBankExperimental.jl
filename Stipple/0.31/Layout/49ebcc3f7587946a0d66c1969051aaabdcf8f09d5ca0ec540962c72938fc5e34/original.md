```
function row(args...; size=-1, xs=-1, sm=-1, md=-1, lg=-1, xl=-1, kwargs...)
```

Creates a `div` HTML element with Quasar's Flexgrid CSS class `row`. Such rows typically contain elements created with [`cell`](@ref), `row`, [`column`](@ref) or other elements that manually receive grid classes, e.g. `"col"`, `"col-sm-5"`.

The grid size kwargs `size`, `xs`, etc. are explained in more detail in the docs of [`cell`](@ref).

### Example

```julia
julia> row(span("Hello"))
"<div class="row"><span>Hello</span></div>"
```

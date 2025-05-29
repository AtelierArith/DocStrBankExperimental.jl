```
function cell(args...; size::Int=0, xs::Int=0, sm::Int=0, md::Int=0, lg::Int=0, xl::Int=0, kwargs...)
```

Creates a `div` HTML element with Quasar's flex grid CSS class `col`. Moreover, cells are of the class `st-col`, which is controlled by the Stipple theme.

If size is specified, the class `col-$size` is added instead.

If tag classes (`xs`, `sm`, `md`, `lg`, `xl`) are specified, the respective classes `col-$tag-$md` are added, e.g. `col-sm-6`.

Parameters:

  * `""` / `0`: shared remaining space (e.g. `"col"`, `"col-sm"`)
  * `1` - `12` / `"1"` - `"12"`: column width (e.g. `"col-5"`, `"col-sm-5"`)
  * `"auto"`/`:auto`: height/width from content (`"col-auto"`, `"col-sm-auto"`)
  * `-1` / `nothing`: no specification

The cells are typically included within [`row`](@ref)s or [`column`](@ref)s. See [Quasar's Flex Grid](https://quasar.dev/layout/grid/introduction-to-flexbox) for more information.

### Example

```julia
julia> row(cell(size = 2, md = 6, sm = 12, span("Hello")))
"<div class="row"><div class="st-col col-2 col-sm-12 col-md-6"><span>Hello</span></div></div>"
```

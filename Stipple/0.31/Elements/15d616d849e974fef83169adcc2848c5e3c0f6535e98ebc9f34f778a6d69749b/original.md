```
@text(expr)
```

Creates a `v-text` or a `text-content.prop` Vue biding to the element's `textContent` property. [https://vuejs.org/v2/api/#v-text](https://vuejs.org/v2/api/#v-text)

### Example

```julia
julia> span("", @text("abc | def"))
"<span :text-content.prop='abc | def'></span>"

julia> span("", @text("abc"))
"<span v-text='abc'></span>"
```

```
@else(expr)
```

Generates `v-else` Vue.js code using `expr` as the condition. [https://vuejs.org/v2/api/#v-else](https://vuejs.org/v2/api/#v-else)

### Example

```julia
julia> span(@else, "Might want to keep an eye on this", class="notice")
"<span v-else class="notice">Might want to keep an eye on this</span>"
```

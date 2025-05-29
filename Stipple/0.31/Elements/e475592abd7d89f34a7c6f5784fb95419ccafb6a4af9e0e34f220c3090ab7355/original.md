```
@elseif(expr)
```

Generates `v-else-if` Vue.js code using `expr` as the condition. [https://vuejs.org/v2/api/#v-else-if](https://vuejs.org/v2/api/#v-else-if)

### Example

```julia
julia> span("An error has occurred", class="error", @elseif(:error))
"<span class="error" v-else-if='error'>An error has occurred</span>"
```

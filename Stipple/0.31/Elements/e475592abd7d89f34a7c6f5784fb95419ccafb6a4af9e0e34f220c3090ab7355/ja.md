```
@elseif(expr)
```

`expr`を条件として使用して`v-else-if` Vue.jsコードを生成します。[https://vuejs.org/v2/api/#v-else-if](https://vuejs.org/v2/api/#v-else-if)

### 例

```julia
julia> span("An error has occurred", class="error", @elseif(:error))
"<span class="error" v-else-if='error'>An error has occurred</span>"
```

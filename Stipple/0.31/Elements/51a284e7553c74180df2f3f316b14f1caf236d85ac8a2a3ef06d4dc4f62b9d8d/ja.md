```
@else(expr)
```

`expr`を条件として使用して`v-else` Vue.jsコードを生成します。[https://vuejs.org/v2/api/#v-else](https://vuejs.org/v2/api/#v-else)

### 例

```julia
julia> span(@else, "Might want to keep an eye on this", class="notice")
"<span v-else class="notice">Might want to keep an eye on this</span>"
```

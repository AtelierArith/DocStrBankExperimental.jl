```
@text(expr)
```

要素の `textContent` プロパティに対する `v-text` または `text-content.prop` Vue バインディングを作成します。 [https://vuejs.org/v2/api/#v-text](https://vuejs.org/v2/api/#v-text)

### 例

```julia
julia> span("", @text("abc | def"))
"<span :text-content.prop='abc | def'></span>"

julia> span("", @text("abc"))
"<span v-text='abc'></span>"
```

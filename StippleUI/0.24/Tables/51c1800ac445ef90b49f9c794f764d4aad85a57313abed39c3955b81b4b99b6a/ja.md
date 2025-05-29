```
Column(name::String, args...)
```

---

### 例

---

```julia-repl
julia> Column("x2", align = :right)
```

---

### 引数

---

  * `required::Bool` - `visiblecolumns`を使用する場合、この列は常に表示されます
  * `label::String` - ヘッダーのラベル
  * `align::Symbol` - セルの配置
  * `field::String` - この列の値を決定する行オブジェクトのプロパティ ex. `name`
  * `sortable::Bool` - `table`にこの列をソート可能にしたいことを伝えます

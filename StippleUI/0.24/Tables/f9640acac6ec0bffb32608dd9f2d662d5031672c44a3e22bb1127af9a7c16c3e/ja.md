```
table(fieldname::Symbol, args...; kwargs...)
```

---

### 例

---

### モデル

```julia-repl
julia> @vars TableModel begin
          data::R{DataTable} = DataTable(DataFrame(rand(100000,2), ["x1", "x2"]), DataTableOptions(columns = [Column("x1"), Column("x2", align = :right)]))
          data_pagination::DataTablePagination = DataTablePagination(rows_per_page=50)
       end
```

### ビュー

```julia-repl
julia> table(:data; pagination=:data_pagination, style="height: 350px;", title="ランダムな数値")
```

スタイリングは、属性 `cell_class`, `cell_style`, `inner_class`, `inner_style`, `change_class`, `change_style`, `inner_change_class`, `inner_change_style` を使用することで実現できます。

```julia
ui() = table(:table, edit = ["name", "email", "age"], cell_type = ["text", "text", "number"])

ui() = table(:table, cell_class = "text-blue-10 bg-blue-2")
```

スタイリングやより複雑なスタイリングに関する詳細は `cell_templates` の下にあります。

手動スタイリングも次のように適用できます：

```julia
table(:table, template(@slot(:body-cell, :props), [
  StippleUI.td(
    textfield("", R"props.row[props.col.name]", :dense, :borderless,
      inputstyle = "font-weight: 400; font-size: 0.9rem; padding-top: 0; padding-bottom: 0"
    )
  )
]))
```

`@slot` マクロの使用に注意してください。これは Stipple v0.28.7 以降で利用可能です。それ以外の場合は `var"v-slot:body-cell" = "props"` を使用してください。

最後に、テーブルはセルをクリックした際のイベント処理をサポートしています。イベントハンドラは `@on()` マクロで追加できます。

```julia
@event :tableclick begin
    @info event
    notify(__model__, "(row, column, value) clicked: ($(event["row"]), $(event["column"]), $(event["value"]))")
end

# クリックされた行の行、列、値、および行データをイベントに追加するため
ui() = table(:table, "Hello world!", @on(:row__clicked, :tableclick, :addTableInfo))`
```

クリックの座標も必要な場合は、次のように追加できます。

```julia
ui() = table(:table, "Hello world!", @on(:row__clicked, :tableclick, [:addTableInfo, :addClickInfo]))
```

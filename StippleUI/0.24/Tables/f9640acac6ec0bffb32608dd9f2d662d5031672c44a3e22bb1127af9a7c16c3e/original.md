```
table(fieldname::Symbol, args...; kwargs...)
```

---

### Examples

---

### Model

```julia-repl
julia> @vars TableModel begin
          data::R{DataTable} = DataTable(DataFrame(rand(100000,2), ["x1", "x2"]), DataTableOptions(columns = [Column("x1"), Column("x2", align = :right)]))
          data_pagination::DataTablePagination = DataTablePagination(rows_per_page=50)
       end
```

### View

```julia-repl
julia> table(:data; pagination=:data_pagination, style="height: 350px;", title="Random numbers")
```

Styling can be achieved by the use of the attributes `cell_class`, `cell_style`, `inner_class`, `inner_style`, `change_class`, `change_style`, `inner_change_class`, `inner_change_style`.

```julia
ui() = table(:table, edit = ["name", "email", "age"], cell_type = ["text", "text", "number"])

ui() = table(:table, cell_class = "text-blue-10 bg-blue-2")
```

More info on styling and more complex styling can be found under `cell_templates`.

Manual styling can also be applied as follows:

```julia
table(:table, template(@slot(:body-cell, :props), [
  StippleUI.td(
    textfield("", R"props.row[props.col.name]", :dense, :borderless,
      inputstyle = "font-weight: 400; font-size: 0.9rem; padding-top: 0; padding-bottom: 0"
    )
  )
]))
```

Note the use of the `@slot` macro, which is available from Stipple v0.28.7 on. Otherwise use `var"v-slot:body-cell" = "props"`.

Finally, table supports eventhandling upon clicking on a cell. The eventhandlers can be added by the `@on()` macro.

```julia
@event :tableclick begin
    @info event
    notify(__model__, "(row, column, value) clicked: ($(event["row"]), $(event["column"]), $(event["value"]))")
end

# for adding row, column, value, and row_data of the clicked row to the event
ui() = table(:table, "Hello world!", @on(:row__clicked, :tableclick, :addTableInfo))`
```

If you also need the coordinates of the click, you can add it via

```julia
ui() = table(:table, "Hello world!", @on(:row__clicked, :tableclick, [:addTableInfo, :addClickInfo]))
```

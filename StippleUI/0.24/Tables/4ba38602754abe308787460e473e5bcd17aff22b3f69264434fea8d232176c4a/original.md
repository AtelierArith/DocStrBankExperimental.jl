```
selectrows!(model::ReactiveModel, tablefield::Symbol, selectionfield::Symbol = Symbol(tablefield, "_selection"), args...)
selectrows!(dt::R{<:DataTable}, dt_selection::R, args...)
```

Select table rows of a model based on selection criteria. More information on selection syntax can be found in `rowselection`

```julia
@vars TableDemo begin
    @mixin table::TableWithPaginationSelection
end

model = init(TableDemo)
model.table[] = DataTable(DataFrame(a = [1, 2, 4, 6, 8, 10], b = ["Hello", "world", ",", "hello", "sun", "!"]))

selectrows!(model, :table, [1, 2, 6]) # assumes the existence of a field `:table_selection`
selectrows!(model.table, model.table_selection, "b", r"hello|World"i)
selectrows!(model, :table, :table_selection, "a", iseven)
```

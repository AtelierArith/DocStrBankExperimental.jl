```
selectrows!(model::ReactiveModel, tablefield::Symbol, selectionfield::Symbol = Symbol(tablefield, "_selection"), args...)
selectrows!(dt::R{<:DataTable}, dt_selection::R, args...)
```

選択基準に基づいてモデルのテーブル行を選択します。選択構文に関する詳細情報は `rowselection` で確認できます。

```julia
@vars TableDemo begin
    @mixin table::TableWithPaginationSelection
end

model = init(TableDemo)
model.table[] = DataTable(DataFrame(a = [1, 2, 4, 6, 8, 10], b = ["Hello", "world", ",", "hello", "sun", "!"]))

selectrows!(model, :table, [1, 2, 6]) # フィールド `:table_selection` の存在を仮定
selectrows!(model.table, model.table_selection, "b", r"hello|World"i)
selectrows!(model, :table, :table_selection, "a", iseven)
```

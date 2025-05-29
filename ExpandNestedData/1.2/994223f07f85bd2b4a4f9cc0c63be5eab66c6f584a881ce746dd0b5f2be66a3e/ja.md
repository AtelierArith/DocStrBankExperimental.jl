```
expand(data, column_defs=nothing;
        default_value = missing,
        lazy_columns::Bool = false,
        pool_arrays::Bool = false,
        column_names::Dict = Dict{Tuple, Symbol}(),
        column_style::Symbol=:flat,
        name_join_pattern = "_")
```

ネストされたデータ構造をテーブルに展開します

## 引数:

  * `data::Any` - アンパックするネストされたデータ
  * `column_defs::Vector{ColumnDefinition}` - `data`内で追跡するパスのリスト。他のブランチは無視します。オプション。デフォルト: `nothing`。

## キーワード引数:

  * `lazy_columns::Bool` - trueの場合、遅延イテレータを使用して列を返します。falseの場合、返す前に通常のベクターに`collect`します。デフォルト: `true`（収集しない）。
  * `pool_arrays::Bool` - trueの場合、列を`collect`するためにプール配列を使用します。デフォルト: `false`。
  * `column_names::Dict{Tuple, Symbol}` - 最終結果の列名を他のシンボルに置き換えるためのルックアップ
  * `column_style::Symbol` - `:nested`または`:flat`から返される列スタイルを選択します。ネストされている場合、`column_names`は無視され、列がソースデータと同じ構造でネストされたTypedTables.Tableが返されます。デフォルト: `:flat`
  * `name_join_pattern::String` - 列名にパスを結合する際にキーの間に置くパターン。デフォルト: `"_"`。

## 戻り値

`column_style = :flat`の場合は`::NamedTuple`、`column_style = :nested`の場合は`TypedTable.Table`。

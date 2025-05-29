```
add_comp!(
    m::Model, comp_def::AbstractComponentDef, comp_name::Symbol=comp_id.comp_name;
    first::NothingInt=nothing,
    last::NothingInt=nothing,
    before::NothingSymbol=nothing,
    after::NothingSymbol=nothing,
    rename::NothingPairList=nothing
)
```

コンポーネント `comp_def` をモデル `m` に追加します。コンポーネントは、キーワード `first`、`last`、`before`、`after` のいずれかが指定されない限り、リストの最後に追加されます。`comp_id` のコピーが作成され、指定された名前が割り当てられます。オプション引数 `rename` は、`original_name => imported_name` を示すペアのリストであることができます。オプション引数 `first` と `last` は、指定されたコンポーネントの実行期間を制約する時間を示し、モデルの範囲内でなければならず、明示的に設定された場合は固定されます。これらはデフォルトでモデルの `:time` 次元に柔軟に変更されます。

```
add_comp!(
    m::Model, comp_id::ComponentId, comp_name::Symbol=comp_id.comp_name;
    first::NothingInt=nothing,
    last::NothingInt=nothing,
    before::NothingSymbol=nothing,
    after::NothingSymbol=nothing,
    rename::NothingPairList=nothing
)
```

`comp_id` で示されるコンポーネントを、`m` で示されるモデルに追加します。コンポーネントは、キーワード `before` または `after` が指定されない限り、リストの最後に追加されます。`comp_id` のコピーがコンポジット内に作成され、指定された名前が割り当てられます。オプションの引数 `rename` は、`original_name => imported_name` を示すペアのリストであることができます。オプションの引数 `first` と `last` は、指定されたコンポーネントの実行期間を制限する時間を示し、モデルの範囲内でなければならず、明示的に設定された場合は固定されます。これらはデフォルトでモデルの `:time` 次元に柔軟に変更されます。

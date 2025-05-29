```
add_comp!(
    obj::AbstractCompositeComponentDef,
    comp_id::ComponentId,
    comp_name::Symbol=comp_id.comp_name;
    first::NothingInt=nothing,
    last::NothingInt=nothing,
    before::NothingSymbol=nothing,
    after::NothingSymbol=nothing,
    rename::NothingPairList=nothing
)
```

`comp_id` で示されるコンポーネントを `obj` で示される複合コンポーネントに追加します。コンポーネントは、キーワード `before` または `after` のいずれかが指定されない限り、リストの最後に追加されます。`comp_id` のコピーが複合体に作成され、指定された名前が割り当てられます。オプションの引数 `first` と `last` は、指定されたコンポーネントの実行期間を制約する時間を示し、モデルの範囲内でなければならず、明示的に設定されている場合は固定されます。これらは、モデルの `:time` 次元に応じて柔軟に変化するのがデフォルトです。

[未実装:] オプションの引数 `rename` は、`original_name => imported_name` を示すペアのリストであることができます。

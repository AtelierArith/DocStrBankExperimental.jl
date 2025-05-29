```
push_item!(
    index::SearchGraph,
    context,
    item;
    push_item=true
)
```

インデックスにオブジェクトを追加します。

引数:

  * `index`: 挿入が行われる検索グラフインデックス
  * `item`: 挿入されるオブジェクトで、インデックス内の他のオブジェクトと同じ空間にあり、距離メトリックによって理解される必要があります。
  * `context`: グラフのコンテキスト環境、[`SearchGraphContext`](@ref)を参照してください。
  * `push_db`: `push_db=false`は内部オプションで、`append!`および`index!`によって使用されます（これは、`item`がすでに挿入されているがインデックスされていないため、データベースに`item`を挿入しないようにします）

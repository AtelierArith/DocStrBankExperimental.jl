```
copy(df::DataFrame; copycols::Bool=true)
```

データフレーム `df` をコピーします。`copycols=true`（デフォルト）であれば、`df` の列ベクトルのコピーを保持する新しい `DataFrame` を返します。`copycols=false` の場合、`df` と列ベクトルを共有する新しい `DataFrame` を返します。

メタデータ: この関数は、すべてのテーブルレベルおよび列レベルのメタデータを保持します。

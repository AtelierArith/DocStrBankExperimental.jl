```
FlexTable(name1 = array1, ...)
```

配列 `array1` などから列名 `name1` などを持つ列ストレージベースの `FlexTable` を作成します。入力配列 `array1` などは、同じ次元とインデックスを共有する必要があります。

`FlexTable` 自体は `AbstractArray` であり、その要素は `(name1 = first(array1), ...)` の形式の `NamedTuple` です。テーブルの行は標準の配列インデックス `table[i]` を介して取得され、列は `table.name` を介して取得されます。

`FlexTable` は `Table` と異なり、列が可変です - `FlexTable` の列を追加、削除、名前変更、置換することができますが、`Table` ではできません。ただし、`Table` はローカルスコープで行にアクセスし、完全に型推論されたコードで反復処理することができるため、`FlexTable` よりも効率的です。

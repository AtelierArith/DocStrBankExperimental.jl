```
Table(name1 = array1, ...)
```

配列 `array1` などから列名 `name1` などを持つ列ストレージベースの `Table` を作成します。入力配列 `array1` などは、同じ次元とインデックスを共有する必要があります。

`Table` 自体は `AbstractArray` であり、その要素は `(name1 = first(array1), ...)` の形式の `NamedTuple` です。テーブルの行は標準の配列インデックス `table[i]` を介して取得され、列は `table.name` を介して取得されます。

`Table` は `FlexTable` と異なり、列は不変です - `FlexTable` では列を追加、削除、名前変更、置き換えることができますが、`Table` ではできません。しかし、`Table` はローカルスコープで行にアクセスし、完全に型推論されたコードで反復処理することができる一方で、`FlexTable` は高階インターフェースでより効率的です。

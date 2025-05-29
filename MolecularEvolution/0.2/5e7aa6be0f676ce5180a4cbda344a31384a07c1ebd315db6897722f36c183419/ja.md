```
populate_tree!(tree::FelNode, starting_message, names, data; init_all_messages = true, tolerate_missing = 1, leaf_name_transform = x -> x)
```

ツリーと `starting_message`（ツリー全体にメッセージを埋め込むためのメモリテンプレートとして機能します）を取ります。`starting_message` はメッセージ（すなわち、パーティションのベクトル）であることができますが、単一のパーティションでも機能します（ただし、ツリーは長さ1のパーティションのベクトルで埋め込まれます）。さらに、`obs2partition` があなたのパーティションタイプに対して実装されている限り、葉ノードは `data` からのデータで埋め込まれ、各葉の名前に一致します。ツリーの葉に名前が `names` のいずれとも一致しない場合、次のようになります。

  * `tolerate_missing = 0` の場合、エラーがスローされます
  * `tolerate_missing = 1` の場合、警告がスローされ、メッセージは非情報的なメッセージに設定されます（`identity!(::Partition)` が定義されている必要があります）
  * `tolerate_missing = 2` の場合、メッセージは非情報的なメッセージに設定され、警告は表示されません（`identity!(::Partition)` が定義されている必要があります）

葉の名前を `names` と一致させる際にツリーからタグを削除するなどのリネーム関数を `leaf_name_transform` に渡すことができます。

```
refresh!(keyset, keyseturl; default_algs)
refresh!(keyset; default_algs)
```

引数:

  * `keyset`: 更新するJWKSet。
  * `keyseturl`: キーを取得するためのURL。

キーワード引数:

  * `default_algs`: 各キータイプに使用するデフォルトアルゴリズムの辞書。

keyseturlからのキーでkeysetを更新します。keyseturlは`http(s)://`または`file://`タイプのいずれかである必要があります。keysetはkeyseturlからのキーで更新され、古いキーは削除されます。

keyseturlが指定されていない場合、keysetに既に設定されているkeyseturlからのキーでkeysetが更新されます。

デフォルトのアルゴリズム値は、keysetが正確なアルゴリズムタイプを指定していない場合にのみ参照されます。例えば、アルゴリズムとして「RSA」のみが指定されている場合、「RS256」が仮定されます。

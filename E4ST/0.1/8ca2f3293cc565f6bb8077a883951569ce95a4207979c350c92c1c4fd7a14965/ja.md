```
Crediting(d::OrderedDict) -> crediting
```

`d`からCrediting構造体を構築します。`d`はモジュール内の設定ファイルから読み込まれたOrderedDictです。Crediting構造体は`d[:type]`の型で、`d`内の他のすべてのキーと値のペアに対するキーワード引数を持っています。

```
Sat(db::AbstractDatabase; dist::SemiMetric=L2Distance(), root=1)
```

メトリックデータ構造を準備します。このコンストラクタを呼び出した後は、`index!`を呼び出してください。

# 引数

  * `db`: インデックスを作成するデータベース

# キーワード引数

  * `dist`: 距離関数、デフォルトはL2Distance()
  * `root`: ルートとして使用されるデータセットの要素

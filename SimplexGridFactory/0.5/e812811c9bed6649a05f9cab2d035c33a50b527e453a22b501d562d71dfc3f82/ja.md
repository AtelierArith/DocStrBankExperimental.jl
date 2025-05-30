```
SimplexGridBuilder(; Generator=nothing,
                     tol=1.0e-12,
                     checkexisting=true)
```

SimplexGridBuilderを作成します。

  * `Generator`: メッシュ生成パッケージに対応するモジュール。有効な選択肢は、対応するJuliaパッケージに関連する`TetGen`と`Triangulate`です。
  * `checkexisting`: 既存のポイントをチェックするかどうか
  * `tol`: この許容範囲内の2つのポイントは、`checkexisting`がtrueの場合にマージされます

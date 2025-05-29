```
addposition!(man::DeMatosCutPruner, position::Matrix)
```

バックワードパス中に以前計算されたカットで領域を更新します。

# 引数

  * `man::DeMatosCutPruner`   更新するプルーナー。
  * `position::Array{T, 2}`   新しい訪問位置、ポイントのコレクションに対応します。

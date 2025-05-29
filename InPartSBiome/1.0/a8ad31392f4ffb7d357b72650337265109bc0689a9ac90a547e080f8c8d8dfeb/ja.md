```
DiskCell3D
```

[`DiskCell`](@ref) の三次元バージョンです。

# 拡張ヘルプ

## フィールドのリスト

  * `id`, `centerpos`, `params`: InPartS 標準フィールド
  * `nodeseparation`: 円形キャップの中心間で測定されたセルのバックボーンの長さ
  * `orientation`: セルの正規化されたバックボーンベクトル
  * `growthprog`: セルの現在の成長段階
  * `grothrate`: `growthprog` の変化率
  * `attached`: true に設定されている場合、すべての自由度の進化（`growthprog` を除く）が停止します。*現在は未使用*。
  * `P`, N: ノードの位置
  * `fP`, `fN`: ノードの力蓄積器

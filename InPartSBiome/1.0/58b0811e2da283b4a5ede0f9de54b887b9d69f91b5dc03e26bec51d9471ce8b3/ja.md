```
DiskCell
```

単純な二次元成長ダンベルモデル。

# 拡張ヘルプ

## フィールドのリスト

  * `id`, `centerpos`, `params`: InPartS 標準フィールド
  * `nodeseparation`: 円形キャップの中心間で測定された細胞バックボーンの長さ
  * `φ`: x軸に対する細胞バックボーンの角度
  * `growthprog`: 細胞の現在の成長段階
  * `grothrate`: `growthprog`の変化率
  * `attached`: trueに設定されている場合、すべての自由度（`growthprog`を除く）の進化が停止します。*現在は未使用*。
  * `P`, N: ノードの位置
  * `fP`, `fN`: ノード力の累積器

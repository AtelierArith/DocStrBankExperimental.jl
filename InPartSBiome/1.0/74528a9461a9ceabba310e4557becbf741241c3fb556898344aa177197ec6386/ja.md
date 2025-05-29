```
RodCell
```

単純な二次元成長するスフェロシリンダー（ディスコレクタングル？）。

モデルの説明については、[J. Isensee et al., J. R. Soc. Interface. 19, 20220512 (2022)](https://doi.org/10.1098/rsif.2022.0512)を参照してください。

# 拡張ヘルプ

## フィールドのリスト

  * `id`, `centerpos`, `params`: InPartS標準フィールド
  * `nodeseparation`: 円形キャップの中心間で測定された細胞バックボーンの長さ
  * `φ`: x軸に対する細胞バックボーンの角度
  * `growthprog`: 細胞の現在の成長段階
  * `grothrate`: `growthprog`の変化率
  * `attached`: trueに設定されている場合、すべての自由度（`growthprog`を除く）の進化が停止します。*現在は未使用*。
  * `backbone`: `LineSegment2D`としてのバックボーンの内部表現
  * `fP`, `fN`: ノード力の累積器

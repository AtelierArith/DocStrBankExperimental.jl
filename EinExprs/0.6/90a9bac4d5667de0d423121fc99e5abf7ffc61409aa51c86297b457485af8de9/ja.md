```
findslices(scorer, path::EinExpr; size, slices, overhead, temperature = 0.01, skip = head(path))
```

条件に従って切断/スライスされるインデックスを検索します。条件は `size`、`overhead`、および `slices` によって満たされます。[`contengra`](https://github.com/jcmgray/cotengra) の `SliceFinder` アルゴリズムに基づく再実装です。

# 引数

  * `scorer` パスと切断の候補インデックスを受け入れ、スコアを返すヒューリスティック関数（またはファンクタ）。
  * `path` テンソルの切断、すなわちスライスのための収縮パスターゲット。

# キーワード引数

  * `size` 指定された場合、スライスの最大中間テンソルはこのサイズ（要素数）を超えません。
  * `slices` 指定された場合、すべての返されたインデックスを切断する際に、少なくとも `slices` 異なるスライスがあります。
  * `overhead` 指定された場合、スライスと元の収縮の間の冗長な操作の量はこの比率を超えません。
  * `temperature` 結果を拡散させるために追加されるボルツマン様ノイズの温度。
  * `skip` スライスの対象としないインデックス。

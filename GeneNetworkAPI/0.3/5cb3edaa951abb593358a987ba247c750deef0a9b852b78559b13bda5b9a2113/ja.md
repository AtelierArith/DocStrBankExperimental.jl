```
run_correlation(trait::String, dataset::String, group::String; tp::String="sample",
                method::String="pearson", n_result::Int64=500,
                gn_url::String=gn_url())
```

この関数は、ターゲットデータベース（`group`）内のすべての特性に対して、`dataset`内の`trait`の相関を計算します。

このクエリは現在、以下のパラメータを取ります：

  * trait (必須): 相関を求める特性ID
  * dataset (必須): 特性が存在するデータセット（短縮形を使用）
  * group (必須): 比較が行われるグループ
  * tp: sample (デフォルト) | tissue
  * method: pearson (デフォルト) | spearman
  * n_result: 返される結果の最大数 (デフォルト = 500)

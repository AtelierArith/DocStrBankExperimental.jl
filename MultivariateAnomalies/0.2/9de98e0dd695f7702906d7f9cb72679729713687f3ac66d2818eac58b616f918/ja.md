```
auc(scores, events, increasing = true)
```

受信者動作特性曲線（AUC）を計算します。これは、出力 `scores` 配列と真の値 (`events`) に基づいています。デフォルトでは、`scores` が増加順に並んでいると仮定されます（`increasing = true`）。つまり、高いスコアはイベントを表します。AUCは、Fawcett, T. (2006) に従って計算されます。ROC分析の紹介。パターン認識レターズ、27(8)、861–874。http://doi.org/10.1016/j.patrec.2005.10.010

# 例

```
julia> scores = rand(10, 2)
julia> events = rand(0:1, 10, 2)
julia> auc(scores, events)
julia> auc(scores, boolevents(events))
```

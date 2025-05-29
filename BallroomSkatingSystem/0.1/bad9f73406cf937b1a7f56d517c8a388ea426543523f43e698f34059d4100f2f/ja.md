```
skating_combined(dances, results_single_dances)
```

ダンス競技における競技者の最終順位をスケーティングルールに基づいて計算します。`dances`はダンスの名前を含む文字列のベクターです。`results_single_dances`は個々のダンスの結果を含むDataFrameのベクターです。正しい入力形式については[`skating_single_dance`](@ref)を参照してください。

出力は、文字列としての累積スケーティングタブローを含むDataFrame、ルール10およびルール11の適用を含むタブローを含むベクター、個々のダンスのスケーティング結果、ならびにスタート番号と最終順位を含むDataFrameです。

```
combined_plots(combined_results::OrderedDict; npart=10)
```

`load_results` 関数から読み込まれた結果の結合プロットを作成します。この関数は、プロットをサイズ `npart` の小さなグループに分割し（デフォルトは 10）、各グループのプロットを垂直に結合します。結合されたプロットの配列を返します。

# 引数

  * `combined_results::OrderedDict`: `load_results` 関数から取得したプロットするデータ。
  * `npart::Int=10`: 単一の垂直グループに結合される最大プロット数。デフォルトは 10。

# 戻り値

  * `Array{Plotly.Plot,1}`: 各要素が最大 `npart` の垂直プロットのグループを表す結合されたプロットオブジェクトの配列。

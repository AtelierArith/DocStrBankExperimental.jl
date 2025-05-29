# `partial_duplication`

タンパク質相互作用ネットワークの進化に基づくランダムグラフモデル。メソッドは無向グラフを取り、既存の頂点をランダムに選択し、ノードを複製し、隣接するエッジを与えられた確率で保持するという手順を実行します。

## 入力

  * 'A::MatrixNetwork{T}': 無向のシードMatrixNetwork。
  * `steps::Int': 手順を実行するステップ数。
  * `p::Float64': 複製後に各エッジを含める確率。

参考文献:      A duplication growth model of gene expression networks      Ashish Bhan, David J Galas, T. Gregory Dewey     https://doi.org/10.1093/bioinformatics/18.11.1486

## 出力

  * 部分複製手順を通じて生成された新しい無向マトリックスネットワーク。
  * 'duplicated_vertices::Array{Int,1}': 複製された頂点のリスト。

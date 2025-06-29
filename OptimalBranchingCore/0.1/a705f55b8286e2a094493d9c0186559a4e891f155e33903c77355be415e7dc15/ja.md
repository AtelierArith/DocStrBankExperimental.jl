```
minimize_γ(table::BranchingTable, candidates::Vector{Clause}, Δρ::Vector, solver)
```

提供された問題サイズ削減のベクトルに基づいて最適なカバーを見つけます。この関数は、反復プロセスを使用したカバー選択アルゴリズムを実装しています。サブカバーの選択を最適化するために整数プログラミングソルバーを利用します。

### 引数

  * `table::BranchingTable`: カバーする必要があるクローズを含む分岐テーブル。テーブルのエントリは、そのビット列のいずれかがクローズを満たす場合にクローズによってカバーされます。詳細については[`covered_by`](@ref)を参照してください。
  * `candidates::Vector{Clause}`: 分岐ルールを形成するための候補クローズのベクトル（[`DNF`](@ref)の形式）。
  * `Δρ::Vector`: 各候補クローズの問題サイズ削減のベクトル。
  * `solver`: 使用されるソルバー。`LPSolver`または`IPSolver`のインスタンスである可能性があります。

### 戻り値

2つの要素のタプル: (選択されたサブセットのインデックス, γ)

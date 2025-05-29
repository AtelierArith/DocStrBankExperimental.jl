SpotAutomaton(w::SpotOmegaWord) SpotAutomaton(d::APDict,[acc::Union{AcceptBuchi,AcceptCoBuchi}],[n::Integer],vs::Pair...)

新しいオートマトンをタイプ `Ta` の文字に対して作成します。引数は次の通りです：

  * `d`、タイプ `Ta` と BDD の間の AP 辞書
  * `acc`、オプションの受理条件（現時点では `AcceptBuchi(n)` と `AcceptCoBuchi(n)` が許可されています）

```

```

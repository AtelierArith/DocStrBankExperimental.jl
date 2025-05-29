```
Muller(; middle = nothing)
```

単変数スカラー関数の根を求めるためのマラー法。

このアルゴリズムは、[Press et al. (2007)](https://numerical.recipes/book.html)のSec. 9.5.2で説明されており、次の根の推定値を見つけるために3点の二次補間を使用する割線法の一般化です。二次補間のため、この方法は複素根を取得するのに適しています。

この方法では、解のための3つの初期推定値`(left, middle, right)`が必要です。推定値`(left, right) = tspan`は`IntervalNonlinearProblem`によって提供され、`middle`の推定値はオプションのキーワード引数として指定できます。他の`BracketingNonlinearSolve.jl`ソルバーとは対照的に、`Muller`アルゴリズムは根を括るために`(left, right)`を必要としません。

### キーワード引数

  * `middle`: 中点の初期推定値。指定されていない場合は、区間`(left, right)`の中点が使用されます。

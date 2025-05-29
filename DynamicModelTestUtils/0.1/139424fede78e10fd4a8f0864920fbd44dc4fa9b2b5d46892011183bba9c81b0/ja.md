```
discretize_solution(solution::SciMLBase.AbstractTimeseriesSolution[, time_ref::SciMLBase.AbstractTimeseriesSolution]; measured=nothing, all_observed=false)
```

`discretize_solution`は、解とオプションの時間参照を受け取り、それをデータフレームに変換します。このデータフレームには、次のいずれかが含まれます：

  * 提供された場合、`measured`に名前が付けられた変数（未知数または観測値）。
  * `all_observed`が`false`で、`measured`が`nothing`の場合、`measured`としてマークされた変数。
  * `all_observed`が`true`で、`measured`が`nothing`の場合、システム内のすべての変数。

データフレームには、各離散化時間のための`timestamp`という列と、各観測値のための列が含まれます。

時間参照が提供されていない場合、`solution`を離散化するために使用される時間基準が代わりに使用されます。

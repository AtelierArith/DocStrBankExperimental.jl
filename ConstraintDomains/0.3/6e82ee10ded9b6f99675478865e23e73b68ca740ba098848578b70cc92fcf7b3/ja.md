Explorer(concepts, domains, objective = nothing; settings = ExploreSettings(domains))

制約充足問題空間を検索するためのExplorerオブジェクトを作成します。

# 引数

  * `concepts`: 各概念関数とその関連する変数インデックスを含むタプルのコレクション。
  * `domains`: 検索空間を表すドメインのコレクション。
  * `objective`: 最適化問題のためのオプションの目的関数。
  * `settings`: 探索プロセスを構成するための`ExploreSettings`オブジェクト。

# 戻り値

探索の準備が整った`Explorer`オブジェクト。

# 例

```julia
domains = [domain([1, 2, 3]), domain([4, 5, 6])]
concepts = [(sum, [1, 2])]
objective = x -> x[1] + x[2]
explorer = Explorer(concepts, domains, objective)
```

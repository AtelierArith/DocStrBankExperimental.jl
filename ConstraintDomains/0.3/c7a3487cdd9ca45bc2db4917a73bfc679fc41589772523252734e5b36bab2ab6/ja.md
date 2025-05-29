```
explore(domains, concept; settings = ExploreSettings(domains), parameters...)
```

ドメインと概念によって定義された探索空間を探索します。

# 引数

  * `domains`: 探索空間を表すドメインのコレクション。
  * `concept`: 制約を定義する概念関数。
  * `settings`: 探索プロセスを構成するための `ExploreSettings` オブジェクト。
  * `parameters`: 概念関数に渡す追加のパラメータ。

# 戻り値

2つのセットを含むタプル: (solutions, non_solutions)。

# 例

```julia
domains = [domain([1, 2, 3]), domain([4, 5, 6])]
solutions, non_solutions = explore(domains, allunique)
```

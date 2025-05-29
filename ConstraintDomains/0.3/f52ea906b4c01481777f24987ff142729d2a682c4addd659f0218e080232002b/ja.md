```
ExploreSettings(
    domains;
    complete_search_limit = 10^6,
    max_samplings = sum(domain_size, domains),
    search = :flexible,
    solutions_limit = floor(Int, sqrt(max_samplings)),
)
```

探索空間を構成するドメインのコレクションの探索設定を作成します。

# 引数

  * `domains`: 探索空間を表すドメインのコレクション。
  * `complete_search_limit`: 完全探索のための探索空間の最大サイズ。
  * `max_samplings`: 部分探索中に取得するサンプルの最大数。
  * `search`: 探索戦略（`:flexible`、`:complete`、または `:partial`）。
  * `solutions_limit`: 保存する解の最大数。

# 戻り値

`ExploreSettings` オブジェクト。

# 例

```julia
domains = [domain([1, 2, 3]), domain([4, 5, 6])]
settings = ExploreSettings(domains, search = :complete)
```

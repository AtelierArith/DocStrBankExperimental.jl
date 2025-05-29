```
Workflow(jobs::AbstractJob...)
```

与えられた一連の `AbstractJob` から `Workflow` を作成します。

`AbstractJob` のリストは完全である必要はなく、私たちのアルゴリズムはすべての接続された `AbstractJob` を自動的に見つけます。

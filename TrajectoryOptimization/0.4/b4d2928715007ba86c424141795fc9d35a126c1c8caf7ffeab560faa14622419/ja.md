```
jacobian!(∇c, con::AbstractConstraint, Z, [inds])
```

全体の軌道に対して制約を評価します。これは、軌道 `Z` に沿って制約を評価するために使用される最も一般的なメソッドであり、他の関数で使用されるべきものです。`inds` 引数は、制約が評価されるノットポイントを決定します。

値は `∇c` に格納され、これは行列の行列である必要があります。もし `con` が `StageConstraint` であれば、`size(∇c,2) = 1` となり、`con` が `CoupledConstraint` であれば `size(∇c,2) = 2` となります。

もし `con` が `StageConstraint` であれば、デフォルトで `jacobian!(∇c, con, z)` が呼び出され、`con` が `CoupledConstraint` であれば `jacobian!(∇c, con, z1, z2, i)` が呼び出されます。

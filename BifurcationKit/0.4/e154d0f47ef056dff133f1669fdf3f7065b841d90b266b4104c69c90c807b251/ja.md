```julia
struct LSFromBLS{Ts} <: BifurcationKit.AbstractLinearSolver
```

この構造体は、次の線形ソルバーを提供するために使用されます。 (1) J⋅x = rhs を解くために、Jをブロックごとに行列で分解し、次に境界戦略を使用して (1) を解きます。

> コレクション / 台形関数に関連する線形システムを解くのに興味深いです。例えば、`BorderingBLS(solver = BK.LSFromBLS(), tol = 1e-9, k = 2, check_precision = true)` を使用します。


  * `solver::Any`: より小さな線形システムを解くために使用される線形ソルバーです。

!!! warn "警告"
    ソルバーは `AbstractMatrix` のみで機能します。


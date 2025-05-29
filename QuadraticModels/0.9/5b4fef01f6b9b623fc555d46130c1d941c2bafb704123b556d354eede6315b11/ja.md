```
sol = postsolve(qm::QuadraticModel{T, S}, psqm::PresolvedQuadraticModel{T, S}, 
                sol_in::QMSolution{S}) where {T, S}
```

元のQP `qm` の解 `sol = (x, y, s_l, s_u)` を、型 [`QMSolution`](@ref) の前処理されたQP (`psqm`) の解 `sol_in` から取得します。`sol_in.s_l` と `sol_in.s_u` はスパースまたはデンスベクトルである可能性がありますが、出力 `sol.s_l` と `sol.s_u` はデンスベクトルです。

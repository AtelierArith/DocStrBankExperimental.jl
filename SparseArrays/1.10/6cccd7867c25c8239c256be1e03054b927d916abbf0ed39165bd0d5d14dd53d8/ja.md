```
spzeros([type], I::AbstractVector, J::AbstractVector, [m, n])
```

構造的ゼロを `S[I[k], J[k]]` に持つ `m x n` のスパース行列 `S` を作成します。

このメソッドは行列のスパースパターンを構築するために使用でき、例えば `sparse(I, J, zeros(length(I)))` を使用するよりも効率的です。

追加のドキュメントと専門的なドライバーについては、`SparseArrays.spzeros!` を参照してください。

!!! compat "Julia 1.10"
    このメソッドはJuliaバージョン1.10以降を必要とします。


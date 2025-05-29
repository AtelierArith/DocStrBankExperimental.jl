```
bandmatrices_eigen(S::Union{SymmetricEigensystem, SkewSymmetricEigensystem}, n::Integer)
```

対称/反対称固有値問題 `L v = λ v` を `B v = 0` の条件の下で一般化された固有値問題 `SA v = λ SB v` に再構成し、`SA` と `SB` のバンド行列の `n × n` 行列表現を返します。`S` が `SymmetricEigensystem` の場合、返される行列は `Symmetric` になります。

!!! note
    システムが対称/反対称であることを確認するテストは行われず、演算子が準拠していることを保証するのはユーザーの責任です。


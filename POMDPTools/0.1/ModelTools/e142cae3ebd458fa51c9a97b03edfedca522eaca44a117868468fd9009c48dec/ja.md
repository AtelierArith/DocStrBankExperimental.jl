```
transition_matrices(m::Union{MDP,POMDP})
transition_matrices(m; sparse=true)
```

(PO)MDP mの遷移行列を構築します。

返されるオブジェクトは、キーがアクションである連想オブジェクト（通常はDict）です。このオブジェクトの各値はAbstractMatrixであり、行は状態インデックスsに対応し、列は状態インデックスs'に対応します。行列のエントリは、状態sから状態s'に遷移する確率です。

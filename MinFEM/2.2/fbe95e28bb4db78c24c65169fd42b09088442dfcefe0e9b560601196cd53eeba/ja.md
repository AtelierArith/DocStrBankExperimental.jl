```
assemble_dirichletcondition_rhs!(
    A::SparseMatrixCSC{Float64, Int64},
    rhs::AbstractVector{Float64},
    DI::Set{Int64},
    bc::AbstractVector{Float64};
    qdim::Int64 = 1
)
```

与えられたディリクレ条件に従って右辺を修正します。動作は `assemble_dirichletcondition!(...)` に似ていますが、システム行列 A は更新されません。これは、システム行列が定数であり、右辺のみが変化する反復アルゴリズムに関連する可能性があります。その場合、修正された行列を保存し、各反復で右辺のみを組み立てることができます。

DI は、条件が有効であるべきノードインデックスのセットである必要があります。ベクトル値の状態の場合、DI はディリクレ条件を持つべき各コンポーネントに設定することができるか、すべてのコンポーネントが条件を持つべき場合は qdim が設定されます。

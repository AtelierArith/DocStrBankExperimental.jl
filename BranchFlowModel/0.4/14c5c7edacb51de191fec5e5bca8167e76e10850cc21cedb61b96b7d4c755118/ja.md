```
solve_metagraph!(mg::MetaGraphsNext.MetaGraph, builder::Function, tol::T; α::T=0.5, verbose=false) where T <: Real
```

MetaGraphsNext.MetaGraph と JuMP モデルを与えられた `builder` メソッドは、`tol` が BranchFlowModel.get_diffs によって提供される差のために満たされるまでモデルを反復的に解決します。

`builder` は、`JuMP.AbstractModel` を返す `CommonOPF.AbstractNetwork` 型の引数を1つだけ受け入れる必要があります。`builder` から返される各モデルは、`mg` の各頂点に `:m` プロパティとして保存されます。

!!! note
    `tol` は、すべての p、q、および v の差の最大絶対値と比較されます。


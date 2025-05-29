```
solve_metagraph!(mg::MetaGraphsNext.MetaGraph, builder::Function, tols::Vector{T}; α::T=0.5, verbose=false) where T <: Real
```

`MetaGraphsNext.MetaGraph` と `JuMP` モデルを与えられた `builder` メソッドは、`BranchFlowModel.get_diffs` によって提供される差が `tols` に満たされるまでモデルを反復的に解決します。

`builder` は、`JuMP.AbstractModel` を返す `CommonOPF.AbstractNetwork` 型の引数を1つだけ受け入れる必要があります。`builder` から返される各モデルは、`mg` の各頂点に `:m` プロパティとして保存されます。

!!! note
    `tols` の長さは3である必要があります。最初の値は実電力の最大絶対差と比較され、2番目は無効電力、3番目は |v| に対して比較されます。すべての差は、リーフ/変電所接続で計算されます。


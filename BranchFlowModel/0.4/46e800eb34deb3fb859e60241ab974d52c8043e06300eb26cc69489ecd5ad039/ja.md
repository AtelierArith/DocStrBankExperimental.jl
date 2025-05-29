```
solve_metagraph!(mg::MetaGraphsNext.MetaGraph, builder::Dict{Int64, Function}, tols::Vector{T}; α::T=0.5, verbose=false) where T <: Real
```

MetaGraphsNext.MetaGraph と JuMP モデル `builder` を与えられた場合、`BranchFlowModel.get_diffs` によって提供された差が満たされるまでモデルを反復的に解決します。`builder` 辞書は、対応する頂点キーの各モデルを構築するために使用されます。

`builder` 辞書内の各関数は、`CommonOPF.AbstractNetwork` 型の引数を1つだけ受け取り、`JuMP.AbstractModel` を返す必要があります。ビルダ関数から返される各モデルは、`mg` の各頂点に `:m` プロパティとして保存されます。

!!! note
    `tols` の長さは3である必要があります。最初の値は実電力の最大絶対差と比較され、2番目は無効電力、3番目は |v| に対して比較されます。すべての差は、葉/変電所接続で計算されます。


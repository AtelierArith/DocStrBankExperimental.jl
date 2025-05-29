```julia
belief_propagate(
    bp::TensorInference.BeliefPropgation;
    kwargs...
) -> Tuple{TensorInference.BPState{T, VT} where {T, VT<:Vector{T}}, TensorInference.BPInfo}

```

信念伝播アルゴリズムを実行し、最終状態と収束に関する情報を返します。

### 引数

  * `bp::BeliefPropgation`: 信念伝播オブジェクト

### キーワード引数

  * `max_iter::Int=100`: 最大反復回数
  * `tol::Float64=1e-6`: 収束のための許容誤差
  * `damping::Float64=0.2`: メッセージ更新のためのダンピング係数、更新されたメッセージ = ダンピング * 古いメッセージ + (1 - ダンピング) * 新しいメッセージ

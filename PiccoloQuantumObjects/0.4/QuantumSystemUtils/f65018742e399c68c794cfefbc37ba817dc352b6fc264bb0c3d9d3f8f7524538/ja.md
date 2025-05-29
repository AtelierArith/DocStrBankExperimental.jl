```
is_reachable(gate, hamiltonians; kwargs...)
```

`gate`が与えられた`hamiltonians`を使用して到達可能かどうかを確認します。

# 引数

  * `gate::AbstractMatrix`: 対象ゲート
  * `hamiltonians::AbstractVector{<:AbstractMatrix}`: リー代数の生成子

# キーワード引数

  * `subspace::AbstractVector{<:Int}=1:size(gate, 1)`: サブスペースインデックス
  * `compute_basis::Bool=true`: 基底を計算するか、ハミルトニアンを直接使用するか
  * `remove_trace::Bool=true`: 生成子からトレースを削除する
  * `verbose::Bool=true`: 演算子代数に関する情報を印刷する
  * `atol::Float32=eps(Float32)`: 絶対許容誤差

他にも [`QuantumSystemUtils.operator_algebra`](@ref) を参照してください。

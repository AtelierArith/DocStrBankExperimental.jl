```julia
empty!(
    lp::SpinGlassTensors.PoolOfProjectors,
    device::Symbol
) -> Union{Nothing, Dict{Int64, Union{Vector{T}, CUDA.CuVector{T}, CUDA.DenseCuVector{T}}} where T<:Integer}

```

特定の計算デバイスに関連付けられたプロジェクタのプールを空にします。

この関数は、指定された計算デバイスに保存されているすべてのプロジェクタを削除し、メモリリソースを解放します。

# 引数:

  * `lp::PoolOfProjectors`: プロジェクタを含む `PoolOfProjectors` オブジェクト。
  * `device::Symbol`: プロジェクタを空にする計算デバイス（例: `:CPU`, `:GPU`）。

```julia
add_projector!(
    lp::SpinGlassTensors.PoolOfProjectors{T<:Integer},
    p::Union{Vector{T}, CUDA.CuArray{T, 1}} where T
) -> Int64

```

`PoolOfProjectors`にプロジェクタを追加し、インデックスに関連付けます。

この関数は、プロジェクタ`p`を`PoolOfProjectors`に追加します。`PoolOfProjectors`は、計算デバイス（例：CPUまたはGPU）に基づいてプロジェクタを保存し、各プロジェクタに一意のインデックスを割り当てます。このインデックスは、後で`get_projector!`を使用してプロジェクタを取得するために使用できます。

# 引数:

  * `lp::PoolOfProjectors{T}`: プロジェクタを追加する`PoolOfProjectors`オブジェクト。
  * `p::Proj`: プールに追加されるプロジェクタ。プロジェクタ`Proj`の型は、`PoolOfProjectors`で指定された型`T`と一致する必要があります。

# 戻り値:

  * `Int`: プールに追加されたプロジェクタに関連付けられた一意のインデックス。

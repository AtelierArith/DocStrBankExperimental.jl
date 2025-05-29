```
ShiftInvariantWaveletTransformObject{N, T₁<:Integer, T₂<:AbstractFloat}
```

信号のすべてのシフト不変ウェーブレット変換（SIWT）情報を保持するデータ構造。

# パラメータ

  * `Nodes::Dict{NTuple{3,T₁}, ShiftInvariantWaveletTransformNode{N,T₁,T₂}}`: ツリー内の各ノードの情報を含む辞書。
  * `SignalSize::Union{T₁, NTuple{N,T₁}}`: 元の信号のサイズ。
  * `MaxTransformLevel::T₁`: 信号のために設定された最大変換レベル。
  * `Wavelet::OrthoFilter`: 変換目的のための離散ウェーブレット。
  * `MinCost::Union{T₂, Nothing}`: 分解ツリーの現在の最小 [`ShannonEntropyCost`](@ref) コスト。

!!! note
    `MinCost` パラメータはデフォルトでルートノードのコストを含みます。分解ツリーの真の最小コストを計算するには、最初に [`bestbasistree`](@ref) を呼び出してSIWTの最適基底を計算する必要があります。


  * `BestTree::Vector{NTuple{3,T₁}}`: 最適基底ツリーに属するノードインデックスのコレクション。

!!! note
    `BestTree` パラメータはデフォルトで全てのノードを含みます。つまり、完全な分解が最適ツリーになります。最小コストを生成するSIWTの最適基底ツリーを取得するには、[`bestbasistree`](@ref) を呼び出す必要があります。


**参照:** [`ShiftInvariantWaveletTransformNode`](@ref)

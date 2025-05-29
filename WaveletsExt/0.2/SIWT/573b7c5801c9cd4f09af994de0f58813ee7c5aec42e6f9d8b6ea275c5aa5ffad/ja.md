```
ShiftInvariantWaveletTransformNode(data, depth, indexAtDepth, transformShift)
```

SIWTノードの外部コンストラクタ。

# 引数

  * `data::Array{T} where T<:AbstractFloat`: コエフィシエントの配列。
  * `depth::S where S<:Integer`: 現在のノードの深さ。
  * `indexAtDepth::S where S<:Integer`: 現在の深さでのノードインデックス。
  * `transformShift::S where S<:Integer`: 変換を計算する前に親ノードに対して行われるシフトのタイプ。
  * `nrm::T where T<:AbstractFloat`: (デフォルト: `norm(data)`) 信号のノルム。

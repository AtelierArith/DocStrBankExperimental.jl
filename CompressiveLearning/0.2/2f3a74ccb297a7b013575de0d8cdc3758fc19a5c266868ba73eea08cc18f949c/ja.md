```julia
struct NyströmSkOp{DT, ET, OT<:Union{CompressiveLearning.Fastfood{DT}, CompressiveLearning.WHOrthoRandom{DT}, AbstractArray{DT, 2}, CompressiveLearning.StructuredLandmarks{DT, BT} where BT}, KT<:Union{CompressiveLearning.Kernel, KernelFunctions.Kernel}} <: CompressiveLearning.LinearSkOp
```

ナイストローム特徴マップに関連する平均埋め込みを計算する演算子。

# フィールド

  * `m::Int64`: 近似に使用されるランドマークポイントの数
  * `d::Int64`: 次元
  * `L::Union{CompressiveLearning.FastTransform, AbstractMatrix{DT}} where DT`: 列がランドマークポイントである線形演算子
  * `K::LinearAlgebra.Symmetric{ET, Matrix{ET}} where ET`: 簡略化されたカーネル行列
  * `K_sqrt_inv::LinearAlgebra.Symmetric{ET, Matrix{ET}} where ET`: 簡略化されたカーネル行列の逆の平方根
  * `k::Union{CompressiveLearning.Kernel, KernelFunctions.Kernel}`: カーネル関数

```julia
struct NyströmSkOp{DT, ET, OT<:Union{CompressiveLearning.Fastfood{DT}, CompressiveLearning.WHOrthoRandom{DT}, AbstractArray{DT, 2}, CompressiveLearning.StructuredLandmarks{DT, BT} where BT}, KT<:Union{CompressiveLearning.Kernel, KernelFunctions.Kernel}} <: CompressiveLearning.LinearSkOp
```

An operator computing the mean embedding associated to a Nyström feature map.

# Fields

  * `m::Int64`: Number of landmark points used for the approximation
  * `d::Int64`: Dimension
  * `L::Union{CompressiveLearning.FastTransform, AbstractMatrix{DT}} where DT`: Linear operator whose columns are landmarks points
  * `K::LinearAlgebra.Symmetric{ET, Matrix{ET}} where ET`: Reduced kernel matrix
  * `K_sqrt_inv::LinearAlgebra.Symmetric{ET, Matrix{ET}} where ET`: Square root of the inverse of the reduced kernel matrix
  * `k::Union{CompressiveLearning.Kernel, KernelFunctions.Kernel}`: Kernel function

```julia
function optimise*linear*sqrtlinear(instance::CombinatorialInstance{T},                                       algo::ESCB2OptimisationAlgorithm,                                       linear::Dict{T, Float64},                                       sqrtlinear::Dict{T, Float64},                                       sqrtlinear*weight::Float64,                                        bandit*round::Int;                                       with_trace::Bool=false) where T

最適化ESCB2の目的関数、線形項（`linear`の係数を持つ）と平方根項（`sqrtlinear`の係数を持つ）を持つ：

max linear^T x + sqrtlinear_weight * sqrt(sqrtlinear^T x)   s.t. xはインスタンスによって定義された組合せ集合に属する

いくつかの実装が提供されており、適切なサブタイプの`ESCB2OptimisationAlgorithm`を使用して選択できます。

1つの（おおよそ）最適な解を返します。正確な保証は選択したアルゴリズムに依存します。`with_trace=true`の場合、アルゴリズムの動作に関する詳細な情報を含む2つ目の値が返されます。
```

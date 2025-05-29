```
variables_node(m, 𝒩ˢⁱⁿᵏ::Vector{<:Sink}, 𝒯, modeltype::EnergyModel)
```

ノードベクターが `Vector{<:Sink}` の場合、需要を満たすためにエネルギーが多すぎる場合（余剰、`:sink_surplus`）や少なすぎる場合（不足、`:sink_deficit`）を定量化するために、両方の変数が作成されます。

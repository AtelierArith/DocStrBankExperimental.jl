```
G2RealSpace(geometry::CubicGrid, σ=1, τ=1; sum_components=false) <: AbstractOperator{SArray}
```

指定された `geometry` における全ての [`Displacements`](@ref) $d⃗$ に対する密度-密度相関の二体演算子です。

$$
    \hat{G}^{(2)}_{σ,τ}(d⃗) = \frac{1}{M} ∑_{i⃗} n̂_{σ,i⃗} (n̂_{τ,i⃗+d⃗} - δ_{0⃗,d⃗}δ_{σ,τ}).
$$

多成分アドレスの場合、`σ` と `τ` は関与する成分を制御します。あるいは、`sum_components` を `true` に設定することで、全ての粒子を同じ成分に属するものとして扱うことができます。

# 例

```jldoctest
julia> geom = CubicGrid(2, 2);

julia> g2 = G2RealSpace(geom)
G2RealSpace(CubicGrid((2, 2), (true, true)), 1,1)

julia> diagonal_element(g2, BoseFS(2,0,1,1))
2×2 StaticArraysCore.SMatrix{2, 2, Float64, 4} with indices SOneTo(2)×SOneTo(2):
 0.5  1.0
 0.5  1.0

julia> g2_cross = G2RealSpace(geom, 1, 2)
G2RealSpace(CubicGrid((2, 2), (true, true)), 1,2)

julia> g2_sum = G2RealSpace(geom, sum_components=true)
G2RealSpace(CubicGrid((2, 2), (true, true)); sum_components=true)

julia> diagonal_element(g2, fs"|⇅⋅↓↑⟩")
2×2 StaticArraysCore.SMatrix{2, 2, Float64, 4} with indices SOneTo(2)×SOneTo(2):
 0.0  0.0
 0.0  0.5

julia> diagonal_element(g2_cross, fs"|⇅⋅↓↑⟩")
2×2 StaticArraysCore.SMatrix{2, 2, Float64, 4} with indices SOneTo(2)×SOneTo(2):
 0.25  0.25
 0.25  0.25

julia> diagonal_element(g2_sum, fs"|⇅⋅↓↑⟩")
2×2 StaticArraysCore.SMatrix{2, 2, Float64, 4} with indices SOneTo(2)×SOneTo(2):
 0.5  1.0
 0.5  1.0
```

# 参照

  * [`CubicGrid`](@ref)
  * [`HubbardRealSpace`](@ref)
  * [`G2RealCorrelator`](@ref)
  * [`G2MomCorrelator`](@ref)
  * [`AbstractOperator`](@ref)
  * [`AllOverlaps`](@ref)

```
ReducedDensityMatrix{T=Float64}(p) <: AbstractObservable{Hermitian{T, Matrix{T}}}
```

`p`-粒子縮小密度行列を計算するために使用できる行列値演算子です。行列要素は次のように定義されます：

$$
\hat{ρ}^{(p)}_{j_1,...,j_1,k_1,...,k_p} =  \prod_{i=1}^{p} â^†_{j_i} \prod_{l=p}^{1} â_{k_{l}}
$$

整数インデックス `j_i` と `k_i` は単一粒子モードを表します。効率のために、これらは異なり、順序付けられています：

$$
j_1 < j_2 < \ldots < j_{p} \quad \land \quad k_1 < k_2 < \ldots < k_{p}
$$

`ReducedDensityMatrix` は、フェルミオンおよびボソンのフォック空間に対して、単一粒子縮小密度行列（`p == 1`）を構築するために使用できます。アドレス型は [`<: SingleComponentFockAddress`](@ref SingleComponentFockAddress) です。`p > 1` の高次の縮小密度行列には、インデックスの順序付けのためにフェルミオンフォックアドレス（[`FermiFS`](@ref)）のみがサポートされています。

`ReducedDensityMatrix` は、[`dot`](@ref) または [`AllOverlaps`](@ref) と共に使用して、全行列を一度に計算することができます。

# 例

```jldoctest
julia> dvec_b = PDVec(BoseFS(1,1) => 0.5, BoseFS(2,0) => 0.5)
2-element PDVec: style = IsDeterministic{Float64}()
  fs"|2 0⟩" => 0.5
  fs"|1 1⟩" => 0.5

julia> Op1 = ReducedDensityMatrix(1)
ReducedDensityMatrix{Float64}(1)

julia> dot(dvec_b, Op1, dvec_b)
2×2 Hermitian{Float64, Matrix{Float64}}:
 0.75      0.353553
 0.353553  0.25

julia> Op2 = ReducedDensityMatrix{Float32}(2)
ReducedDensityMatrix{Float32}(2)

julia> dot(dvec_b, Op2, dvec_b)
ERROR: ArgumentError: ReducedDensityMatrix(p) with `p > 1` requires `FermiFS` addresses

julia> dvec_f = PDVec(FermiFS(1,1,0,0) => 0.5, FermiFS(0,1,1,0) => 0.5)
2-element PDVec: style = IsDeterministic{Float64}()
  fs"|⋅↑↑⋅⟩" => 0.5
  fs"|↑↑⋅⋅⟩" => 0.5

julia> dot(dvec_f, Op2, dvec_f)
6×6 Hermitian{Float32, Matrix{Float32}}:
 0.25  0.0  0.25  0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
 0.25  0.0  0.25  0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
 0.0   0.0  0.0   0.0  0.0  0.0
```

[`single_particle_density`](@ref)、[`SingleParticleDensity`](@ref)、[`SingleParticleExcitation`](@ref)、[`TwoParticleExcitation`](@ref) も参照してください。

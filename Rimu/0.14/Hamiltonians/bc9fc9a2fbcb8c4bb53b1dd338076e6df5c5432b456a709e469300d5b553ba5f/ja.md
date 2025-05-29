```
ParticleNumberOperator() <: AbstractOperator{Float64}
```

フォック空間における数演算子。この演算子はフォック基底において対角であり、フォック状態における粒子の数を返します。これは、[`AbstractFockAddress`](@ref) のサブタイプである任意のアドレス型で動作します。

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> p = ExactDiagonalizationProblem(FroehlichPolaron(fs"|0 0⟩{}"; mode_cutoff=5, v=3));

julia> gs = solve(p).vectors[1]; # 正規化された基底状態ベクトル

julia> dot(gs, ParticleNumberOperator(), gs) # 粒子数の期待値
2.8823297252925917
```

関連情報として [`AbstractHamiltonian`](@ref) を参照してください。

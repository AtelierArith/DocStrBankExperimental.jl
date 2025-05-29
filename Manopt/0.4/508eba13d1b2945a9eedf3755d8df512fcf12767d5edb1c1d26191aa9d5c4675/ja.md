```
particle_swarm!(M, f, swarm; kwargs...)
particle_swarm!(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
```

粒子群最適化アルゴリズム (PSO) を実行し、初期の `swarm` から始めて、インプレースで修正されます。

# 入力

  * `M`:     マンフォールド $\mathcal M$
  * `f`:     最小化するコスト関数 $f:\mathcal M→ℝ$
  * `swarm`: （`[rand(M) for _ in 1:swarm_size]`）初期の点の群。

コスト関数 `f` の代わりに、[`AbstractManifoldCostObjective`](@ref) `mco` を提供することもできます。

詳細およびオプションの引数については、[`particle_swarm`](@ref) を参照してください。

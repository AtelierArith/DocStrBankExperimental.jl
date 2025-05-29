```
atomic_measure(ν::MomentMatrix, rank_check::RankCheck, [dec::LowRankLDLTAlgorithm], [solver::SemialgebraicSets.AbstractAlgebraicSolver])
```

原子である場合は `ν` の原子を持つ `AtomicMeasure` を返し、`ν` が原子でない場合は `nothing` を返します。`rank_check` と `dec` パラメータは [`low_rank_ldlt`](@ref) 関数にそのまま渡されます。デフォルトでは、`dec` は [`SVDLDLT`](@ref) のインスタンスです。抽出は代数方程式の系の解に依存しています。`solver` を使用します。例えば、[`MomentMatrix`](@ref) `μ` が与えられた場合、次のように `rank_check` を `1e-4` に設定して低ランク分解を行い、得られた代数方程式の系を解くためにホモトピー継続を使用して原子を抽出します。

```julia
using HomotopyContinuation
solver = SemialgebraicSetsHCSolver(; compile = false)
atoms = atomic_measure(ν, 1e-4, solver)
```

ソルバーが指定されていない場合、SemialgebraicSets のデフォルトソルバーが使用され、現在はグローバー基底を計算し、その後、乗算行列を計算し、これらの行列のランダムな組み合わせのシュール分解を行います。浮動小数点算術の場合、ホモトピー継続が推奨されます。なぜなら、グローバー基底計算よりも数値的に安定しているからです。

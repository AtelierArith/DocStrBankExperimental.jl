```
CrossPairs(;
    xpositions::AbstractVector{<:AbstractVector{T}},
    ypositions::AbstractVector{<:AbstractVector{T}},
    cutoff::T,
    unitcell::AbstractVecOrMat,
    xn_atoms_per_molecule::Int,
    parallel::Bool=true
) where T<:Real
```

1つの分子と他の分子のセットとの間の最小距離を計算するための粒子システムを初期化します。参照分子に対する各分子のセットの最も近い距離に関する情報を含む最小距離のリスト（`MinimumDistance`型）を返します。

分子あたりの原子の数の代わりに、ユーザーはより一般的な`mol_indices`関数を提供することもでき、これは各原子インデックスに対して対応する分子インデックスを返します（すべての分子が同じ数の原子を持ち、位置の配列に連続して格納されている場合、`mol_indices(i) = (i-1)%n + 1`となります）。

# 例

```julia-repl
julia> using MolecularMinimumDistances, StaticArrays

julia> sys = CrossPairs(
           xpositions=rand(SVector{3,Float64},10^5), # "溶媒"（分子のセット）
           ypositions=rand(SVector{3,Float64},1000), # "溶質"（ターゲット構造）
           cutoff=0.1,
           unitcell=[1,1,1],
           xn_atoms_per_molecule=5 # "溶媒"の
       )
CrossPairsシステム:

セットの原子数: 100000
ターゲット構造の原子数: 1000
カットオフ: 0.1
ユニットセル: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]
セットの分子数: 20000

julia> minimum_distances!(sys)
20000要素のVector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 1, 859, 0.037219109441123784)
 MinimumDistance{Float64}(true, 10, 117, 0.042183794688796634)
 ⋮
 MinimumDistance{Float64}(true, 99996, 168, 0.014269620784984633)
```

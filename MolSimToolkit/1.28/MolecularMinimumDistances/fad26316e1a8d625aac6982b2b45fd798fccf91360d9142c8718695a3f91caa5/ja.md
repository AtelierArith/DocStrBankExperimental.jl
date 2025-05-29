```
AllPairs(;
    xpositions::AbstractVector{<:AbstractVector{<:Real}},
    ypositions::AbstractVector{<:AbstractVector{<:Real}},
    cutoff::Real,
    unitcell::AbstractVecOrMat,
    xn_atoms_per_molecule::Integer,
    yn_atoms_per_molecule::Integer,
    parallel::Bool=true
)
```

1つの分子と他の分子のセットとの間の最小距離を計算するための粒子システムを初期化します。参照分子に対する最も近い距離に関する情報を含む最小距離のリスト（`MinimumDistance`型）を返します。

分子あたりの原子数の代わりに、ユーザーはより一般的な`xmol_indices`および/または`ymol_indices`関数を提供することもでき、これは各原子インデックスに対して対応する分子インデックスを返します（すべての分子が同じ数の原子を持ち、位置の配列に連続して格納されている場合、`mol_indices(i) = (i-1)%n + 1`であり、`n`は分子あたりの原子数です）。

# 例

```julia-repl
julia> using MolSimToolkit, StaticArrays

julia> sys = AllPairs(
           xpositions=rand(SVector{3,Float64},10^5), # "溶媒"（分子のセット）
           ypositions=rand(SVector{3,Float64},1000), # "溶質"（ターゲット構造）
           cutoff=0.1,
           unitcell=[1,1,1],
           xn_atoms_per_molecule=5, # "溶媒"の
           yn_atoms_per_molecule=10 # "溶媒"の
       )
AllPairsシステム:

最初のセットの原子数: 100000
最初のセットの分子数: 20000

2番目のセットの原子数: 1000
2番目のセットの分子数: 100

カットオフ: 0.1
単位セル: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]

julia> minimum_distances!(sys)[1]
20000要素のVector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 1, 859, 0.037219109441123784)
 MinimumDistance{Float64}(true, 10, 117, 0.042183794688796634)
 ⋮
 MinimumDistance{Float64}(true, 99996, 168, 0.014269620784984633)
```

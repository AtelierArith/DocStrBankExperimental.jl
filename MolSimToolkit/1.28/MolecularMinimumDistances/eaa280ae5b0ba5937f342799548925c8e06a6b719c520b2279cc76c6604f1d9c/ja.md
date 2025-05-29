```
CrossPairs(;
    xpositions::AbstractVector{<:AbstractVector{<:Real}},
    ypositions::AbstractVector{<:AbstractVector{<:Real}},
    cutoff::Real,
    unitcell::AbstractVecOrMat,
    xn_atoms_per_molecule::Integer,
    parallel::Bool=true
)
```

1つの分子と他の分子のセットとの間の最小距離を計算するための粒子システムを初期化します。参照分子に対する最も近い距離に関する情報を含む、セットの各分子に対する最小距離（`MinimumDistance`型）のリストを返します。

分子あたりの原子の数の代わりに、ユーザーはより一般的な`mol_indices`関数を提供することもでき、これは各原子インデックスに対して対応する分子インデックスを返します（すべての分子が同じ数の原子を持ち、位置の配列に連続して格納されている場合、`mol_indices(i) = (i-1)%n + 1`であり、`n`は分子あたりの原子の数です）。

# 例

```julia-repl
julia> using MolSimToolkit, StaticArrays

julia> sys = CrossPairs(
           xpositions=rand(SVector{3,Float64},10^5), # "溶媒"（分子のセット）
           ypositions=rand(SVector{3,Float64},1000), # "溶質"（ターゲット構造）
           cutoff=0.1,
           unitcell=[1,1,1],
           xn_atoms_per_molecule=5 # "溶媒"の
       )
CrossPairsシステム:

セットの原子の数: 100000
ターゲット構造の原子の数: 1000
カットオフ: 0.1
ユニットセル: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]
セットの分子の数: 20000

julia> minimum_distances!(sys)
20000要素のベクトル{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 1, 859, 0.037219109441123784)
 MinimumDistance{Float64}(true, 10, 117, 0.042183794688796634)
 ⋮
 MinimumDistance{Float64}(true, 99996, 168, 0.014269620784984633)
```

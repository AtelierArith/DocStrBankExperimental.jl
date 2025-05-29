```
SelfPairs(;
    xpositions::AbstractVector{<:AbstractVector{<:Real}},
    cutoff::Real,
    unitcell::AbstractVecOrMat,
    xn_atoms_per_molecule::Integer,
    parallel::Bool=true
) where T<:Real
```

単一の分子セット内での最小距離の計算のために粒子システムを初期化します。同じセットの他の分子への各分子の最短距離が計算されます。

分子あたりの原子数の代わりに、ユーザーはより一般的な `mol_indices` 関数を提供することもでき、これは各原子インデックスに対して対応する分子インデックスを返します（すべての分子が同じ数の原子を持ち、位置の配列に連続して格納されている場合、`mol_indices(i) = (i-1)%n + 1` であり、ここで `n` は分子あたりの原子数です）。

# 例

```julia-repl
julia> using MolSimToolkit, StaticArrays

julia> sys = SelfPairs(
           xpositions=rand(SVector{3,Float64},10^5),
           cutoff=0.1,
           unitcell=[1,1,1],
           xn_atoms_per_molecule=5
       )
SelfPairs system with:

Number of atoms: 100000
Cutoff: 0.1
unitcell: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]
Number of molecules: 20000

julia> minimum_distances!(sys)
20000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 4, 24930, 0.008039482961077074)
 MinimumDistance{Float64}(true, 6, 74055, 0.0049818659155905255)
 ⋮
 MinimumDistance{Float64}(true, 99999, 75403, 0.0025051670801269433)
```

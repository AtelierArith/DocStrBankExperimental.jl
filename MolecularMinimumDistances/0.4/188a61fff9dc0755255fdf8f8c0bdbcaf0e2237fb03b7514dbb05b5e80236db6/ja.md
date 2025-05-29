```
minimum_distances!(system)
```

初期化されたシステムの最小距離を計算する関数で、`SelfPairs`、`CrossPairs`、または`AllPairs`タイプのものです。

この関数は、`SelfPairs`および`CrossPairs`入力に対して`Vector{MinimumDistance}`を返し、`AllPairs`入力タイプに対してはそのようなベクトルのタプルを返します。

この関数は、事前に割り当てられたシステム入力からの高度な代替手段として使用されます。`minimum_distances!`の呼び出し時には、主にマルチスレッド計算の開始に関連するいくつかの割り当てが残ります。

# 例

```julia-repl
julia> using MolecularMinimumDistances, StaticArrays

julia> sys = SelfPairs(
           xpositions = rand(SVector{3,Float64},1000), 
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10,
       )
SelfPairsシステムの情報:

原子の数: 1000
カットオフ: 0.1
unitcell: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]
分子の数: 100

julia> minimum_distances!(sys)
100要素のVector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 8, 579, 0.03570387474690425)
 MinimumDistance{Float64}(true, 12, 534, 0.02850448652684309)
 ⋮
 MinimumDistance{Float64}(true, 996, 423, 0.03655145613454862)

julia> using BenchmarkTools

julia> @btime minimum_distances!($sys);
  178.468 μs (209 allocations: 22.80 KiB)
```

```
function minimum_distances(
   xpositions::AbstractVector{<:SVector},
   # または xpositions *および* ypositions (CrossPairs または AllPairs)
   cutoff=0.1,
   unitcell=[1,1,1],
   xn_atoms_per_molecule=5
   # または xn_atoms_per_molecule (CrossPairs)
   # または xn_atoms_per_molecule *および* yn_atoms_per_molecule (AllPairs)
)
```

この関数は、粒子のセット内の最小距離を直接計算します。提供された入力位置配列の数と分子インデックス情報の数に応じて、異なるタイプの計算が行われます：

  * `xpositions` と `xn_atoms_per_molecule` が提供されている場合、提供されたセットの分子内の最小距離が計算されます。
  * `xpositions` と `ypositions` が提供され、**のみ** `xn_atoms_per_molecule` が提供されている場合、セット `x` の分子の最小距離がセット `y` に対して計算されます（言い換えれば、`ypositions` は単一の構造と見なされます）
  * `xpositions` と `ypositions` が提供され、`xn_atoms_per_molecule` **および** `yn_atoms_per_molecule` が与えられている場合、`x` の各分子から `y` の任意の原子までの最小距離が計算され、逆も同様です。最小距離のベクトルのタプルが返され、長さはそれぞれセット `x` と `y` の分子の数に対応します。

他の関数がコンストラクタであるのと同様に、`xn_atoms_per_molecule` キーワードパラメータは、各原子の分子インデックスを返す一般的な関数に置き換えることができます（すなわち、最も単純でデフォルトのケースでは `(i) -> (i-1)%n_atoms_per_molecule + 1`）。

# 例

## 単一の分子セット：セット内のすべての最小距離

出力には、セットの分子の数に等しい長さの `MinimumDistance` 要素のベクトルが含まれていることに注意してください。

```julia-repl
julia> using MolecularMinimumDistances, StaticArrays

julia> list = minimum_distances(
           xpositions = rand(SVector{3,Float64},10^5), 
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10)
10000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 5, 71282, 0.007669490894775502)
 MinimumDistance{Float64}(true, 19, 36374, 0.005280726329888545)
 ⋮
 MinimumDistance{Float64}(true, 99998, 44320, 0.006509632622462869)
```

## 2つのセット：1つのセットの最小距離を他のセットに対して計算

出力には、`x` セットの分子の数が含まれていることに注意してください。このセットの各分子について、セット `y` への最小距離が計算されます。これは典型的な「溶質-溶媒」の例であり、`x` には溶媒の位置が含まれ、`y` には溶質の位置が含まれます。

```julia-repl
julia> list = minimum_distances(
           xpositions = rand(SVector{3,Float64},10^5), 
           ypositions = rand(SVector{3,Float64},10^3),
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10,
       )
10000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 5, 596, 0.025526453519907292)
 MinimumDistance{Float64}(true, 18, 391, 0.014114699969628301)
 ⋮
 MinimumDistance{Float64}(true, 99993, 289, 0.016089848937890512)
```

## 2つのセット：分子間のすべての最小距離を計算

両方のセットの分子の数が `xn_atoms_per_molecule` および `yn_atoms_per_molecule` キーワードで提供されると、両方のセットが分子に分割され、すべての最小距離が計算されます。各セットの各分子について、他のセットの任意の他の分子への最小距離が返されます。出力はリストのタプルです。

```julia-repl
julia> lists = minimum_distances(
           xpositions = rand(SVector{3,Float64},10^5), 
           ypositions = rand(SVector{3,Float64},10^3),
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10,
           yn_atoms_per_molecule=100
       );

julia> lists[1]
10000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 10, 471, 0.03211876310646438)
 MinimumDistance{Float64}(true, 13, 113, 0.0364141004391549)
 ⋮
 MinimumDistance{Float64}(true, 99992, 673, 0.0345818388567913)

julia> lists[2]
10-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 81, 754, 0.002292544732548094)
 MinimumDistance{Float64}(true, 156, 17208, 0.0018147268509811352)
 ⋮
 MinimumDistance{Float64}(true, 944, 98048, 0.002902338025311851)
```

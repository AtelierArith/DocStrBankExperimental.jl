```
xf₀ = find_energy_minimum_gridsearch(xtal, molecule, ljff; resolution=(50, 50, 50))
```

[`energy_grid`](@ref) 計算を実行し、グリッドサーチを介して分子の最小エネルギー位置を見つけます。

# 引数

  * `xtal::Crystal`: 調査中の結晶
  * `molecule::Molecule{Cart}`: エネルギー表面を探るために使用される分子
  * `ljff::LJForceField`: 相互作用エネルギーを計算するために使用される力場
  * `resolution::Union{Float64, Tuple{Int, Int, Int}}=1.0`: グリッドポイント間の最大距離（Å単位）または各次元のグリッドポイント数を指定するタプル。

# 戻り値

  * `minimized_molecule::Molecule{Frac}`: 最小エネルギー位置にある分子
  * `min_energy::Float64`: 関連する最小分子-結晶相互作用エネルギー (kJ/mol)

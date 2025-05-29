```
minimized_molecule, min_energy  = find_energy_minimum(xtal, molecule, ljff) # molecule set at initial guess
```

結晶中の分子の最小エネルギー位置と関連する最小エネルギーを見つけます。注意：分子に原子が複数ある場合、*回転*に関しては最小化されません。最適化プログラムは最小エネルギー位置の初期推定が必要です。良い初期位置を持つ分子を渡してください。良い初期位置がない場合は、[`find_energy_minimum_gridsearch`](@ref)を使用してください。

# 引数

  * `xtal::Crystal`: 結晶
  * `molecule::Molecule`: 位置を調整して局所最小値に達することを求める分子。最小値に近い良い初期位置から始める必要があります。
  * `ljff::LJForceField`: 結晶-分子相互作用エネルギーを計算するために使用される力場

# 戻り値

  * `minimized_molecule::Molecule{Frac}`: 最小エネルギー位置にある分子
  * `min_energy::Float64`: 関連する最小分子-結晶相互作用エネルギー (kJ/mol)

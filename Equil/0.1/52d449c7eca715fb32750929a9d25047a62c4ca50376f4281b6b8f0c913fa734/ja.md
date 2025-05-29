この関数は、入力フィルターから読み取った初期条件に基づいて平衡組成を計算します。

# 使用法

```
equilibrate(input_file::AbstractString, lib_dir::AbstractString)
```

  * input_file ; T、p、種のリスト、モル分率を指定する入力xmlファイル
  * lib_dir : therm.datファイルが存在するフォルダー

また、ユーザー入力に基づいて同じことを計算することもでき、種の組成が辞書として渡されます。

# 使用法

```
equilibrate(T::Float64, p::Float64, species_comp::Dict{String, Float64}, thermo_obj)
```

  * T : 温度（K）
  * p : 圧力（Pa）
  * thermo*obj : IdealGas.create*thermoを使用して作成された熱力学オブジェクト
  * species_comp : 種の組成の辞書 {String, Float64}

また、ユーザー入力に基づいて同じことを計算することもでき、種のリストとモル分率が別々の配列として渡されます。

# 使用法

```
equilibrate(T, p, thermo_obj, mole_fracs, gasphase)
```

  * T : 温度（K）
  * p : 圧力（Pa）
  * thermo*obj : IdealGas.create*thermoを使用して作成された熱力学オブジェクト
  * mole_fracs : 種のモル分率
  * gasphase : ガス相種のリスト

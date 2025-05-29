H(thermo::NASAThermo, T::Float64) 純粋な種のエンタルピーを計算します J/mol

# 使用法-1:

```
H(thermo,T)
```

  * 'thermo::NASAThermo': 種のNASAThermo
  * 'T::Float64': 必要な特性の温度（K）

# 使用法-2:

```
H(sp,T,thermo,ig)
```

  * sp::String : 種の名前
  * T::Float64 : 温度（K）
  * thermoObj::SpeciesThermoObj : SpeciesThermoObjの構造
  * species_list::Array{String,1}  : 種のリスト

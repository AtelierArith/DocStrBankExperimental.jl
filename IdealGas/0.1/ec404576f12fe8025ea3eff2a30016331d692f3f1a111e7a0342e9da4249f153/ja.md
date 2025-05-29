S(thermo::NASAThermo, T::Float64) 純粋な種のエントロピーを計算します J/mol-K

# 使用法-1:

```
S(thermo,T)
```

  * thermo::NASAThermo: 種のNASAThermo
  * T::Float64: 必要な特性の温度（K）

# 使用法-2:

```
S(sp,T,thermo,ig)
```

  * sp::String : 種の名前
  * T::Float64 : 温度（K）
  * thermo::SpeciesThermoObj : SpeciesThermoObjの構造
  * species_list::Array{String,1}  : 種のリスト

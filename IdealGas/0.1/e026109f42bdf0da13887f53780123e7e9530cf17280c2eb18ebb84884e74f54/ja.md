純物質の比熱を計算する J/mol-K

# 使用法-1:

```
cp(thermo,T)
```

  * thermo::NASAThermo: 物質のNASAThermo
  * T::Float64: 必要な性質の温度（K）

# 使用法-2:

```
cp(sp,T,thermo,ig)
```

  * sp::String : 物質名
  * T::Float64 : 温度（K）
  * thermoObj::SpeciesThermoObj : SpeciesThermoObjの構造
  * species_list::Array{String,1}  : 物質のリスト

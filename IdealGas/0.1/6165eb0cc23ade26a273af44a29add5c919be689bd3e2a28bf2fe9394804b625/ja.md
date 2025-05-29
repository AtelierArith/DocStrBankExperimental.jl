Smix(thermoObj::SpeciesThermoObj,T::Float64,p::Float64,mlf::Array{Float64,1}) 混合物のエントロピーを J/mol-K で計算します。

# 使用法

```
Smix(thermoObj,T,p,mlf)
```

  * 'thermoObj::SpeciesThermoObj' : SpeciesThermoObj の構造
  * 'T::Float64' : 温度 (K)
  * 'p::Float64' : 総圧 (Pa)
  * 'mlf::Array{Float64,1} ': モル分率

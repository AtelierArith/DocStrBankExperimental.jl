```
get_phase(composition::Union{Silicic,Mafic}, P::Float64, T::Float64, V::Float64, rho_m::Float64, M_h2o::Float64, M_co2::Float64, eps_x0::Float64)::NamedTuple{(:phase, :m_co2_melt),NTuple{2,Float64}}
```

  * この関数は、初期相を決定するために `IC_Finder` 関数内で使用されます。

## 戻り値

以下のフィールドを持つ NamedTuple:

  * `phase`: 2 または 3
  * `m_co2_melt`

```
set_reference_state(fluid::AbstractString, T::Real, rhomolar::Real, hmolar0::Real, smolar0::Real)
```

温度とモル密度で指定された熱力学的状態点に基づいて参照状態を設定します。

#引数

  * `fluid::AbstractString`	流体の名前
  * `T::Real`	参照状態の温度 [K]
  * `rhomolar::Real`	参照状態のモル密度 [mol/m^3]
  * `hmolar0::Real`	参照状態のモルエンタルピー [J/mol]
  * `smolar0::Real`	参照状態のモルエントロピー [J/mol/K]

#Ref set*reference*stateD(const char* Ref, double T, double rhomolar, double hmolar0, double smolar0) ```

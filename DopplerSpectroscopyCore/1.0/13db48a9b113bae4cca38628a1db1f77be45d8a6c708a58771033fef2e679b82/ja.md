```
Quantum2Level
```

量子二準位系をそのシステムのパラメータを通じて説明するクラス。

# フィールド

  * `mass` :   量子システムの質量の値を表す (kg)。
  * `temperature` :   量子システムの温度の値を表す (K)。
  * `relax_sp` :   量子システムにおける自発光周波数の値を表し、このモデルでは定数と見なされ、他の文書および以下では `γ₀` と呼ばれる (Hz)。
  * `relax_opt` :   量子システムにおける光遷移の光学的放出周波数の値を表し、このモデルでは定数と見なされる (単位は `γ₀`)。
  * `dimmless_velocity` :   無次元単位での量子システムの最も可能性の高い速度の値を表す。

# 引数

  * `M`, `T`, `γ₀`, `γₒₚₜ` :   フィールドの説明を参照。
  * `light` :   量子二準位系と相互作用するために使用される光源。

# 戻り値

  * `Quantum2Level` :   複合型インスタンス。

# 参照

  * [`LightSource`](@ref)

# 参考文献

  * Wikipedia: https://en.wikipedia.org/wiki/Density_matrix
  * Wikipedia: https://en.wikipedia.org/wiki/Spontaneous_emission

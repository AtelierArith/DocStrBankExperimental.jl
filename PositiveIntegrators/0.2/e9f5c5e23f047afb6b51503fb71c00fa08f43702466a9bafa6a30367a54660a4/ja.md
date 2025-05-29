```
MPRK22(α; [linsolve = ..., small_constant = ...])
```

生産-消滅システムのための二次改良パタンカールンゲクッタアルゴリズムのファミリーです。このファミリーの各メンバーは、適応型の1ステップ2段階の手法であり、二次精度を持ち、無条件に正の値を保持し、線形暗黙的です。この実装では、ステージ値も保守的です。パラメータ `α` はKopeczとMeister（2018）によって説明され、Izgin、Kopecz、Meister（2022）およびTorlo、Öffner、Ranocha（2022）によって研究されています。

この手法は、パタンカール重みの分母 $σ_i$ を使用して適応的な時間ステッピングをサポートし、KopeczとMeister（2018）を参照して、誤差を推定するための一次近似として機能します。

このスキームは、保守的な生産-消滅システムのためにKopeczとMeisterによって導入されました。非保守的な生産-消滅システムの場合は、[`MPE`](@ref) に類似した直接的な拡張を使用します。

この改良パタンカールンゲクッタ法は、[`PDSProblem`](@ref) または [`ConservativePDSProblem`](@ref) の特別な構造を必要とします。

オプションで、キーワード引数 `linsolve` として [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) からアルゴリズムを渡すことで使用する線形ソルバーを選択できます。また、すべてのパタンカール重みの分母に追加されるパラメータ `small_constant` を選択することもできます。明示的に値を渡すことができますが、そうでない場合は `small_constant` は使用される浮動小数点型の `floatmin` に設定されます。

## 参考文献

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
  * Stefan Kopecz and Andreas Meister. "On order conditions for modified Patankar-Runge-Kutta schemes." Applied Numerical Mathematics 123 (2018): 159-179. [DOI: 10.1016/j.apnum.2017.09.004](https://doi.org/10.1016/j.apnum.2017.09.004)
  * Thomas Izgin, Stefan Kopecz, and Andreas Meister. "On Lyapunov stability of positive and conservative time integrators and application to second order modified Patankar-Runge-Kutta schemes." ESAIM: Mathematical Modelling and Numerical Analysis 56.3 (2022): 1053-1080. [DOI: 10.1051/m2an/2022031](https://doi.org/10.1051/m2an/2022031)
  * Davide Torlo, Philipp Öffner, and Hendrik Ranocha. "Issues with positivity-preserving Patankar-type schemes." Applied Numerical Mathematics 182 (2022): 117-147. [DOI: 10.1016/j.apnum.2022.07.014](https://doi.org/10.1016/j.apnum.2022.07.014)

```
SSPMPRK43([linsolve = ..., small_constant = ...])
```

生産-破壊システムのための三次改良パタンカール-ルンゲ-クッタ法。このスキームは、三次精度を持ち、無条件に正の保持をし、線形的に暗黙的な一段階四段階法です。このスキームは、Huang、Zhao、Shu（2019）によって説明され、Huang、Izgin、Kopecz、Meister、Shu（2023）によって研究されました。[`MPRK43I`](@ref)や[`MPRK43II`](@ref)との違いは、この方法が明示的な三次ルンゲ-クッタ法のSSP定式化に基づいていることです。

このスキームは、保守的な生産-破壊システムのためにHuang、Zhao、Shuによって導入されました。非保守的な生産-破壊システムの場合は、[`MPE`](@ref)に類似した直接的な拡張を使用します。

この改良パタンカール-ルンゲ-クッタ法は、[`PDSProblem`](@ref)または[`ConservativePDSProblem`](@ref)の特別な構造を必要とします。

オプションで、キーワード引数`linsolve`として[LinearSolve.jl](https://github.com/SciML/LinearSolve.jl)からアルゴリズムを渡すことで使用する線形ソルバーを選択できます。また、ゼロ除算を避けるために、すべてのパタンカール重みの分母に追加されるパラメータ`small_constant`を選択することもできます。データ型`type`のデフォルト値を表示するには、`SSPMPRK43.small_constant_function(type)`を評価します。ここで、`type`は例えば`Float64`などです。

現在の実装は固定時間ステップのみをサポートしています。

## 参考文献

  * Juntao Huang, Weifeng Zhao and Chi-Wang Shu. "A Third-Order Unconditionally Positivity-Preserving Scheme for Production–Destruction Equations with Applications to Non-equilibrium Flows." Journal of Scientific Computing 79 (2019): 1015–1056 [DOI: 10.1007/s10915-018-0881-9](https://doi.org/10.1007/s10915-018-0881-9)
  * Juntao Huang, Thomas Izgin, Stefan Kopecz, Andreas Meister and Chi-Wang Shu. "On the stability of strong-stability-preserving modified Patankar-Runge-Kutta schemes." ESAIM: Mathematical Modelling and Numerical Analysis 57 (2023):1063–1086 [DOI: 10.1051/m2an/2023005](https://doi.org/10.1051/m2an/2023005)

```
SSPMPRK22(α, β; [linsolve = ..., small_constant = ...])
```

生産-破壊システムのための二次改良パタンカール-ルンゲ-クッタ法のファミリーです。このファミリーの各メンバーは、適応型の1ステップ2段階の手法であり、二次精度を持ち、無条件に正の値を保持し、線形暗黙的です。パラメータ `α` と `β` はHuangとShu（2019）によって説明され、Huang、Izgin、Kopecz、Meister、Shu（2023）によって研究されています。 [`MPRK22`](@ref)との違いは、この手法が明示的な二次ルンゲ-クッタ法のSSP定式化に基づいていることです。このスキームのファミリーには、`MPRK22(α) = SSMPRK22(0, α)` が適用される [`MPRK22`](@ref) ファミリーが含まれています。

この手法は、最初のオーダー近似 $(σ_i - u_i^n) / τ + u_i^n$ を使用して適応的な時間ステッピングをサポートします。ここで、$τ=1+(α_{21}β_{10}^2)/(β_{20}+β_{21})$ であり、HuangとShu（2019）の（2.7）を参照してください。

このスキームは、保守的な生産-破壊システムのためにHuangとShuによって導入されました。非保守的な生産-破壊システムの場合は、[`MPE`](@ref) に類似した直接的な拡張を使用します。

この改良パタンカール-ルンゲ-クッタ法は、[`PDSProblem`](@ref) または [`ConservativePDSProblem`](@ref) の特別な構造を必要とします。

オプションで、キーワード引数 `linsolve` として [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) からアルゴリズムを渡すことで使用する線形ソルバーを選択できます。また、ゼロ除算を避けるためにすべてのパタンカール重みの分母に追加されるパラメータ `small_constant` を選択することもできます。値を明示的に渡すことができますが、そうでない場合は `small_constant` は使用される浮動小数点型の `floatmin` に設定されます。

## 参考文献

  * Juntao Huang and Chi-Wang Shu. "Positivity-Preserving Time Discretizations for Production–Destruction Equations with Applications to Non-equilibrium Flows." Journal of Scientific Computing 78 (2019): 1811–1839 [DOI: 10.1007/s10915-018-0852-1](https://doi.org/10.1007/s10915-018-0852-1)
  * Juntao Huang, Thomas Izgin, Stefan Kopecz, Andreas Meister and Chi-Wang Shu. "On the stability of strong-stability-preserving modified Patankar-Runge-Kutta schemes." ESAIM: Mathematical Modelling and Numerical Analysis 57 (2023):1063–1086 [DOI: 10.1051/m2an/2023005](https://doi.org/10.1051/m2an/2023005)

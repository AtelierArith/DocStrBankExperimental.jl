```
tcRK(components::Vector{String};
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false,
estimate_alpha = true,
estimate_translation = true)
```

翻訳された一貫したレドリッヒ・クワン方程式です。以下のモデルを使用します：

  * 翻訳モデル: [`ConstantTranslation`](@ref)
  * アルファモデル: [`TwuAlpha`](@ref)
  * 混合則モデル: [`vdW1fRule`](@ref)

Twuパラメータが提供されていない場合、非中心因子（`acentricfactor`）から推定できます。翻訳が提供されていない場合、Rackett圧縮因子（`ZRA`）または非中心因子（`acentricfactor`）を使用して推定できます。

アルファ関数と体積翻訳の推定の使用は、`estimate_alpha = false`または`estimate_translation = false`を渡すことで無効にできます。

## 参考文献

1. Le Guennec, Y., Privat, R., & Jaubert, J.-N. (2016). Development of the translated-consistent tc-PR and tc-RK cubic equations of state for a safe and accurate prediction of volumetric, energetic and saturation properties of pure compounds in the sub- and super-critical domains. Fluid Phase Equilibria, 429, 301–312. [doi:10.1016/j.fluid.2016.09.003](http://dx.doi.org/10.1016/j.fluid.2016.09.003)
2. Pina-Martinez, A., Le Guennec, Y., Privat, R., Jaubert, J.-N., & Mathias, P. M. (2018). Analysis of the combinations of property data that are suitable for a safe estimation of consistent twu α-function parameters: Updated parameter values for the translated-consistent tc-PR and tc-RK cubic equations of state. Journal of Chemical and Engineering Data, 63(10), 3980–3988. [doi:10.1021/acs.jced.8b00640](http://dx.doi.org/10.1021/acs.jced.8b00640)
3. Piña-Martinez, A., Privat, R., & Jaubert, J.-N. (2022). Use of 300,000 pseudo‐experimental data over 1800 pure fluids to assess the performance of four cubic equations of state: SRK , PR , tc ‐RK , and tc ‐PR. AIChE Journal. American Institute of Chemical Engineers, 68(2). [doi:10.1002/aic.17518](https://doi.org/10.1021/acs.iecr.1c03003)

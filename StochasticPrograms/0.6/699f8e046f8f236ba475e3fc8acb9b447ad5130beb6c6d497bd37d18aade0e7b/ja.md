```
WS(stochasticprogram::TwoStageStochasticProgram, scenario::AbstractScenarioaData; optimizer = nothing)
```

二段階`stochasticprogram`の**待機観察**（`WS`）モデルを生成し、`scenario`に対応します。

言い換えれば、`scenario`が発生することが知られているかのように、`stochasticprogram`の第一段階と第二段階を生成します。オプションとして、`WS`に適した`optimizer`を提供することができます。

参照: [`DEP`](@ref), [`EVP`](@ref)

```
EVP(stochasticprogram::TwoStageStochasticProgram; optimizer = nothing)
```

二段階 `stochasticprogram` の **期待値問題** (`EVP`) を生成します。

言い換えれば、`stochasticprogram` におけるすべての利用可能なシナリオに対する期待シナリオに対応する待機モデルを生成します。オプションとして、能力のある `optimizer` を `WS` に供給することができます。

参照: [`expected_value_decision`](@ref), [`EEV`](@ref), [`EV`](@ref), [`WS`](@ref)

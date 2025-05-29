```
DEP(stochasticprogram::TwoStageStochasticProgram; optimizer = nothing)
```

二段階 `stochasticprogram` の **決定論的に同等な問題** (`DEP`) を生成します。キャッシュされたバージョンが既に存在しない場合に限ります。

言い換えれば、`stochasticprogram` の拡張形式を単一の JuMP モデルとして生成します。オプションで、適切な `optimizer` を `DEP` に供給することができます。

参照: [`VRP`](@ref), [`WS`](@ref)

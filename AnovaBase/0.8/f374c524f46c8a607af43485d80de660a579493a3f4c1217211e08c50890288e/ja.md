```
anovatable(aov::AnovaResult{<: FullModel, Test}; rownames = prednames(aov))
anovatable(aov::AnovaResult{<: MultiAovModels, Test}; rownames = string.(1:N))
anovatable(aov::AnovaResult{<: MultiAovModels, FTest, N}; rownames = string.(1:N)) where N
anovatable(aov::AnovaResult{<: MultiAovModels, LRT, N}; rownames = string.(1:N)) where N
```

ANOVAの係数と関連統計を含むテーブルを返します。

`repl`で`aov`を表示する際、`rownames`は[`FullModel`](@ref)の場合は`prednames(aov)`、[`MultiAovModels`](@ref)の場合は`string.(1:N)`になります。

`MultiAovModels`の場合、`FTest`と`LRT`の2つのデフォルトメソッドがあり、`::AnovaResult{NestedModels{M}}`または`::AnovaResult{MixedAovModels{M}}`に基づいて新しいメソッドを定義することもできます。ここで、`M`はモデルタイプです。

`FullModel`の場合、デフォルトのAPIは実装されていません。

返される`AnovaTable`オブジェクトは[`Tables.jl`](https://github.com/JuliaData/Tables.jl/)インターフェースを実装しており、例えば`using DataFrames; DataFrame(anovatable(aov))`を通じてDataFrameに変換できます。

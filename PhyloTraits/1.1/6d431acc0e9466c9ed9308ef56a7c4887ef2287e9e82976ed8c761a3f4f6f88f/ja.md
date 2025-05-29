```
TwoBinaryTraitSubstitutionModel(rate [, label])
```

[`TraitSubstitutionModel`](@ref) は、相関のある可能性のある2つの二項特性のためのものです。デフォルトのラベルは、特性1に対して "x0"、"x1"、特性2に対して "y0"、"y1" です。提供される場合、`label` はサイズ4のベクトルで、特性1のラベルを最初に、次に特性2のラベルをリストする必要があります。`rate` はサイズ8の置換率のベクトルである必要があります。rate[1],...,rate[4] は特性1の変化率を説明し、rate[5],...,rate[8] は特性2の変化率を説明します。遷移行列では、特性の組み合わせは次の順序でリストされます: x0-y0, x0-y1, x1-y0, x1-y1。

# 例

```julia
model = TwoBinaryTraitSubstitutionModel([2.0,1.2,1.1,2.2,1.0,3.1,2.0,1.1],
        ["carnivory", "noncarnivory", "wet", "dry"]);
model
using PhyloPlots
plot(model) # 状態と率を視覚化するため。PhyloPlots v2.0.0 ではサポートされていません。PhyloPlots v1.0.0 が必要です。
```

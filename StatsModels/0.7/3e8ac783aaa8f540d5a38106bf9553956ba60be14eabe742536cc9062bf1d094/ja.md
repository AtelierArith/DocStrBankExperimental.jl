```
termnames(model::StatisticalModel)
```

`model`の式で使用される項の名前を返します。

これは`termnames(formula(model))`の便利なメソッドであり、式の左辺と右辺に適用された`termnames`の2タプルを返します。

連続的な予測因子のみを持つ`RegressionModel`の場合、これは`(responsename(model), coefnames(model))`および`coefnames(formula(model))`と同じです。

カテゴリカル予測因子を持つモデルの場合、返される名前は変数名を反映し、コントラストコーディングの選択から得られる係数ではありません。

[`coefnames`](@ref)も参照してください。

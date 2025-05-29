```
ActivationContribution{L,C,M} <: AbstractMutableComp
ActivationContribution(l)
ActivationContribution(l, method)
```

活性化と勾配に基づいてニューロンのユーティリティを`method`を使用して計算します。

[`fluxvertex`](@ref)への`layerfun`引数として使用するように設計されています。

大きな活性化がある場合、パフォーマンスのボトルネックになる可能性があります。これを軽減するために[`NeuronUtilityEvery`](@ref)を使用してください。

デフォルトの`method`は[https://arxiv.org/abs/1611.06440](https://arxiv.org/abs/1611.06440)で説明されています。

短い要約は、最適化問題の一次テイラー近似は「どのニューロンを削除すれば損失関数への影響を最小化できるか？」という問いに帰着し、「`abs(gradient * activation)`を最小化するニューロン」となります（パラメータの独立性を仮定しています）。

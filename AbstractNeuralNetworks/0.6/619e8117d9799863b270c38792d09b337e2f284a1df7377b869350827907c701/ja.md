```
AbstractPullback{NNLT<:NetworkLoss}
```

`AbstractPullback` は、`GeometricMachineLearning` における微分（特にニューラルネットワークのパラメータに関する勾配の計算）を行うすべての方法を包含する `abstract type` です。

ユーザーがカスタム `Pullback` を実装したい場合、次の2つの関数を拡張する必要があります：

```julia
(_pullback::AbstractPullback)(ps, model, input_nt_output_nt::Tuple{<:QPTOAT, <:QPTOAT})
(_pullback::AbstractPullback)(ps, model, input_nt::QPT)
```

これは、`_pullback` に格納されている `loss::NetworkLoss` に基づいています。_pullback の出力は、次の内容を含む `Tuple` である必要があります：

1. `ps` と `input_nt`（または `input_nt_output_nt`）で評価された `loss`、
2. `ps` に関する `loss` の勾配で、例えば次のように呼び出すことができます：

```julia
_pullback(ps, model, input_nt)[2](1) # `ps` に関する勾配を返します
```

$$
\ldots
$$

この規約は、`Zygote` がプルバックを構築する方法に類似しているため使用されます。

例として `GeometricMachineLearning.ZygotePullback` があります。

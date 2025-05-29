```
createθ(m::MixedModel; named_re)
create_theta(m::MixedModel; named_re)
```

ランダム効果に対応するパラメータベクトル θ を作成します。

`named_re` は [`create_re`](@ref) を使用して作成できます。`named_re` はブロッキング変数の名前によって指定されます。例えば、`subj=create_re(...)` のように指定します。

モデルは、パラメータが計算効率のために内部でソートされるため、指定する必要があります。

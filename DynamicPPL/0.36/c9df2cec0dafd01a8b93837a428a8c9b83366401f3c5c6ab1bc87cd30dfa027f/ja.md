```
tilde_assume(context::SamplingContext, right, vn, vi)
```

仮定された変数を処理します。例えば、`x ~ Normal()`（ここで`x`はモデルの入力に含まれます）では、対数確率を累積し、サンプラーに関連付けられたコンテキストと共にサンプリングされた値を返します。

次のようにフォールバックします。

```julia
tilde_assume(context.rng, context.context, context.sampler, right, vn, vi)
```

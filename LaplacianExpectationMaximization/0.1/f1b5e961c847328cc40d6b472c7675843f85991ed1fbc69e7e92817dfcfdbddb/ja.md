```
Optimizer(; optimizer = OptimOptimizer(Optim.LBFGS()), finetuner = nothing, fallback = OptimisersOptimizer())
```

デフォルトのオプティマイザ。`finetuner` は最初の `optimizer` が終了した後に呼び出される別のオプティマイザである可能性があります。`fallback` オプティマイザは、`optimizer` または `finetuner` が失敗した場合に呼び出されます。

次のようにも構築できます。

```
Optimizer(optimizer; finetuner = nothing, fallback = OptimisersOptimizer(), kw...)
```

ここで `optimizer` はシンボル（NLoptを使用するため）またはOptimまたはOptimiserからのオプティマイザである可能性があります。詳細については、[`NLoptOptimizer`](@ref)、[`OptimOptimizer`](@ref)、[`OptimisersOptimizer`](@ref)を参照してください。

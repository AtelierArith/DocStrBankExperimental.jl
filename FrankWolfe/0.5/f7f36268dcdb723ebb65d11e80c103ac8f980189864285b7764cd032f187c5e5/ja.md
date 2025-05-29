```
lazified_conditional_gradient(f, grad!, lmo_base, x0; ...)
```

[`FrankWolfe.frank_wolfe`](@ref)と似ていますが、LMOを遅延評価します：各呼び出しはキャッシュに保存され、十分な方向が見つかるまで最初にキャッシュが参照されます。使用されるキャッシュは、提供された`cache_size`オプションが有限であるかどうかに応じて、[`FrankWolfe.MultiCacheLMO`](@ref)または[`FrankWolfe.VectorCacheLMO`](@ref)です。

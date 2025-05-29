```
evaluate(f,x...)
```

は、内部で一時的なキャッシュを作成することによって、引数 `x` に対してマッピング `f` を評価します。この関数は次のものと同等です。

```jl
cache = return_cache(f,x...)
evaluate!(cache,f,x...)
```

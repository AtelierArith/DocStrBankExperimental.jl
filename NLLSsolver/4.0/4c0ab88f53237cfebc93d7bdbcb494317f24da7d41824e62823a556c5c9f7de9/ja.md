```
NLLSsolver.nullcallback(cost, problem, data, iteratedata)
```

何もしないコールバックで、タプル `(cost, 0)` を返します。

# 例

次のようにNLLSsolverの問題を最適化します：

```julia
    NLLSsolver.optimize!(problem, options, unfixed, nullcallback)
```

コールバックのオーバーヘッドは発生しません。

!!! note
    これは `optimize!` によって使用されるデフォルトのコールバックです。


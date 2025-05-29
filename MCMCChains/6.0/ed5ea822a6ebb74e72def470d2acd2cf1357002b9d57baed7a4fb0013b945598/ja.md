```
ess(chains::Chains; duration=compute_duration, kwargs...)
```

有効サンプルサイズを推定します。

ESS毎秒のオプションには `duration=MCMCChains.compute_duration`（デフォルト）と `duration=MCMCChains.wall_duration` が含まれます。

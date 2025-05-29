```
wait(
    cond::Function,
    job::BatchJob;
    timeout=600,
    delay=5
)
```

バッチジョブの状態を `cond` の条件のいずれかに達するまでポーリングします。ループは `failure` 条件に達した場合に終了し、例外はキャッチしません。ポーリング間隔は `delay` で制御でき、`timeout` は最大ポーリング時間を提供します。

# 例

```julia
julia> wait(state -> state < SUCCEEDED, job)
true
```

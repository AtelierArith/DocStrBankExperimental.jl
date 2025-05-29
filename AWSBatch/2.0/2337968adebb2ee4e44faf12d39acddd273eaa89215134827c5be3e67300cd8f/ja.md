```
wait(
    job::BatchJob,
    cond::Vector{JobState}=[RUNNING, SUCCEEDED],
    failure::Vector{JobState}=[FAILED];
    kwargs...,
)
```

バッチジョブの状態をポーリングして、`cond`のいずれかの条件に達するまで待機します。ループは`failure`条件に達した場合に終了し、例外はキャッチしません。ポーリング間隔は`delay`で制御でき、`timeout`は最大ポーリング時間を提供します。

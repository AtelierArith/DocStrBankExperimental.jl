```
next(dc::DirectCall, when::TimeType, rng::AbstractRNG)
```

サンプラーに次に発火する時計とその時刻を尋ねます。これはサンプラーを変更しません。これを複数回呼び出して、複数の回答を得ることができます。各回答は `(when, which clock)` のタプルです。発火する時計がない場合、応答は `(Inf, nothing)` になります。これはシミュレーションが完了した良い兆候です。

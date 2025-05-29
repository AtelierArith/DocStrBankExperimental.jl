```
construct_strategy_cache(mp::Union{IntervalProbabilities, IntervalMarkovProcess}, config::AbstractStrategyConfig)
```

与えられた区間マルコフ過程の構成から戦略キャッシュを構築します。生成されるキャッシュのタイプは構成に依存し、戦略を保存するデバイスはマルコフ過程のデバイスに依存します。

```
score_components(a::ScoringFunction, cpd::CPD, data::DataFrame)
score_components(a::ScoringFunction, cpds::Vector{CPD}, data::DataFrame, cache::ScoreComponentCache)
```

すべてのcpdのスコアコンポーネントのリストを取得します。

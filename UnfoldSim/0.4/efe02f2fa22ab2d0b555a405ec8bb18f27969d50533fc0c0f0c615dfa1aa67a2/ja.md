```
generate_events(design::AbstractDesign)
generate_events(rng::AbstractRNG, design::AbstractDesign)
```

実験条件と設計で定義された共変量に基づいて、フルファクタリアルイベントのDataFrameを生成します。

# 引数

  * `design::AbstractDesign`: イベントDataFrameを作成するための実験デザイン。
  * `rng::AbstractRNG`（オプション）: プロセスを再現可能にするための乱数生成器（RNG）。指定がない場合は、`MersenneTwister(1)`が使用されます。

# 戻り値

  * `DataFrame`: 各行は条件/共変量レベルの1つの組み合わせに対応し、これはしばしば1つの刺激または試行に相当します。

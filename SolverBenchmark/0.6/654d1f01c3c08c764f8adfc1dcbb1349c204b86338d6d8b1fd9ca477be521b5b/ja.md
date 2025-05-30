```
performance_profile(stats, cost, args...; b = PlotsBackend(), kwargs...)
```

`cost`関数を使用して`stats`内のソルバーを比較するパフォーマンスプロファイルを生成します。

入力:

  * `stats::Dict{Symbol,DataFrame}`: `:solver => df`のペア;
  * `cost::Function`: 各`df`に適用されるコスト関数。各行で問題を解くコストを持つベクトルを返す必要があります;

      * 0コストは許可されていません;
      * ソルバーが問題を解決しなかった場合、Infまたは負の数を返します。
  * `b::BenchmarkProfiles.AbstractBackend` : プロットに使用されるバックエンド。

コスト関数の例:

  * `cost(df) = df.elapsed_time`: シンプルな`elapsed_time`コスト。ソルバーが問題を解決したと仮定します。
  * `cost(df) = (df.status .!= :first_order) * Inf + df.elapsed_time`: ソルバーのステータスを考慮に入れます。

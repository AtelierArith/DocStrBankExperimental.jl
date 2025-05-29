```
scale_op_sp(t_inv::TS.AbstractStrategicPeriod, t::TS.TimePeriod)
```

戦略的期間と運用期間が結合されているときに、乗算を返すための簡略化された関数を提供します。

$$
duration(t) * multiple\_strat(t\_inv, t) * probability(t)
$$

これは、運用期間に提供された値を戦略的期間の1の期間にスケーリングするために使用されます。

# 例

```julia
# それぞれ4年間の期間を持つ2つの戦略的期間を表す時間構造と
# 時間解像度が時間単位で1週間を含む
ts = TwoLevel(2, 4, SimpleTimes(168,1); op_per_strat=8760.0);

# 最初の戦略的期間とその最初の運用期間を抽出
t_inv = first(strat_periods(ts))
t = first(t_inv)

# 値を52.14（1年の週数）として計算
scale_op_sp(t_inv, t)
```

```
profit(anp::AbstractNewsvendorProblem)
```

在庫数量 q_opt のときの期待利益を計算します。

```
profit(anp::AbstractNewsvendorProblem, q)
```

在庫数量 q のときの期待利益を計算します。これは次のように与えられます。

$$
E[\textrm{profit}] = \textrm{underage cost} \times  \mu - E[\textrm{mismatch cost}] +  \textrm{profit shift}
$$

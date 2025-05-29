```
mismatch_cost(anp::AbstractNewsvendorProblem, q)
```

在庫数量 q のときの期待されるミスマッチコストを計算します。これは次のように与えられます。

$$
E[\textrm{ミスマッチコスト}] = \textrm{不足コスト} \times  E[\textrm{失われた販売}] + \textrm{過剰コスト} \times  E[\textrm{残り}]
$$

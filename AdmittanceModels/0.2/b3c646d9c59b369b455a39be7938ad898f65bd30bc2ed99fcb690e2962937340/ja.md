```
canonical_gauge(pso::PSOModel)
canonical_gauge(bbox::Blackbox)
```

可逆変換を適用して、モデルを `P` が `[I ; 0]` となる座標に移します（浮動小数点誤差を考慮）。これにより、密なモデルが作成されます。

```
solve(
    problem::GeneralBTPDE,
    gradient,
    odesolver = QNDF();
    abstol = 1e-6,
    reltol = 1e-4,
    callbacks = [].
)
```

空間でP1有限要素を使用し、時間で`odesolver`を使用してBloch-Torrey偏微分方程式を解きます。

```
solve(problem::HADC, gradient::ScalarGradient, odesolver = QNDF();
    abstol = 1e-6,
    reltol = 1e-4,
)
```

ホモジナイズされたADCモデル（HADC）を使用してADCを計算します。これは現在、スカラー勾配に対してのみ実装されています。

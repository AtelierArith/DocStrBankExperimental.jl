```
prox!(reg::TVRegularization, x, λ)
```

TV正則化のための近接写像。TVが1次元のみで計算される場合はCondatアルゴリズムで計算され、それ以外の場合は高速勾配投影アルゴリズムで計算されます。

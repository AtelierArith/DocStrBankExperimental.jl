```
vals = hess_coord!(nlp, x, y, vals; obj_weight=1.0)
```

点 `(x,y)` でのラグランジアンヘッセ行列をスパース座標形式で評価し、目的関数は `obj_weight` でスケーリングされます。すなわち、

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

ここで `σ = obj_weight` であり、`vals` を上書きします。下三角のみが返されます。

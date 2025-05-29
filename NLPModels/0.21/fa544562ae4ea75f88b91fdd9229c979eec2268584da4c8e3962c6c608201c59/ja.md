```
vals = hess_coord!(nlp, x, vals; obj_weight=1.0)
```

点 `x` での目的のヘッセ行列をスパース座標形式で評価し、目的関数は `obj_weight` でスケーリングされます。すなわち、

$$
σ ∇²f(x),
$$

ここで `σ = obj_weight` であり、`vals` を上書きします。下三角のみが返されます。

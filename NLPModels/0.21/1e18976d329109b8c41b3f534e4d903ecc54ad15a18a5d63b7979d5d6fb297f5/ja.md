```
vals = hess_coord(nlp, x; obj_weight=1.0)
```

`x`における目的関数のヘッセ行列をスパース座標形式で評価し、目的関数は`obj_weight`でスケーリングされます。すなわち、

$$
σ ∇²f(x),
$$

ここで、`σ = obj_weight`です。下三角のみが返されます。

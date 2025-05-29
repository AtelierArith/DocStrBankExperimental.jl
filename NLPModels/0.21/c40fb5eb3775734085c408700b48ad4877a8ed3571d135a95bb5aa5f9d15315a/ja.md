```
Hx = hess(nlp, x; obj_weight=1.0)
```

点 `x` での目的ヘッセ行列をスパース行列として評価し、目的関数は `obj_weight` でスケーリングされます。すなわち、

$$
σ ∇²f(x),
$$

ここで `σ = obj_weight` です。下三角をラップした `Symmetric` オブジェクトが返されます。

```
Hx = hess(nlp, x, y; obj_weight=1.0)
```

点 `(x,y)` でラグランジアンヘッセ行列をスパース行列として評価します。目的関数は `obj_weight` でスケーリングされます。すなわち、

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

ここで `σ = obj_weight` です。下三角をラップした `Symmetric` オブジェクトが返されます。

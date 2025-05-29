```
H = hess_op(nlp, x, y; obj_weight=1.0)
```

Lagrangian Hessianを`(x,y)`で返し、目的関数は`obj_weight`でスケーリングされ、線形演算子として扱われます。結果のオブジェクトは行列のように使用できます。例えば、`H * v`のように。線形演算子Hは次のように表されます。

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

ここで`σ = obj_weight`です。

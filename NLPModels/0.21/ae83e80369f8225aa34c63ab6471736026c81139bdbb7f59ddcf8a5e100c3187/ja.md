```
H = hess_op(nlp, x; obj_weight=1.0)
```

目的関数を `obj_weight` でスケーリングした状態で、点 `x` における目的のヘッセ行列を線形演算子として返します。結果のオブジェクトは、行列のように使用できます。例えば、`H * v` のように使用します。線形演算子 H は次のように表されます。

$$
σ ∇²f(x),
$$

ここで `σ = obj_weight` です。

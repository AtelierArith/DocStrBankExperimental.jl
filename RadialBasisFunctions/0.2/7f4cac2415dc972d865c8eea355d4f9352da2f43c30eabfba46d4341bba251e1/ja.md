```
function partial(data, eval_points, order, dim, basis; k=autoselect_k(data, basis))
```

`RadialBasisOperator`を構築します。この演算子は偏微分であり、`Partial`です。結果として得られる演算子は、`eval_points`でのみ評価されます。

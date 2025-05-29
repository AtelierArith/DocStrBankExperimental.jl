```
function gradient(data, eval_points, basis; k=autoselect_k(data, basis))
```

`RadialBasisOperator`を構築します。この演算子は勾配であり、`Gradient`です。結果として得られる演算子は`eval_points`でのみ評価されます。

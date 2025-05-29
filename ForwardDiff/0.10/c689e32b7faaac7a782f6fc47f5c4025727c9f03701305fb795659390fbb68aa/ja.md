```
ForwardDiff.derivative(f, x::Real)
```

`df/dx`を`x`で評価した結果を返します。`f`は`f(x)`として呼び出されると仮定します。

このメソッドは`isa(f(x), Union{Real,AbstractArray})`であると仮定します。

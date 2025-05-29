```
apply(op, ::State; limits::Limits)
apply(mps, ::State; limits::Limits)
apply(op, ::Simulation; limits::Limits)
```

与えられたゲートを状態に適用し、制限に従って結果を切り捨てます。すべてのゲートを単一のapply呼び出しで適用する方がはるかに効率的です。

# 例

```
apply(CZ(1,3)*H(2)*CNOT(3,4), state)
```

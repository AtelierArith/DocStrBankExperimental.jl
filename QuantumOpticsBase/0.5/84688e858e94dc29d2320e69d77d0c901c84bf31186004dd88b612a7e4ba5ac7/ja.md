```
LazyProduct(operators[, factor=1])
LazyProduct(op1, op2...)
```

演算子の積の遅延評価。

積の因子は `operators` フィールドに格納されます。さらに、複素因子は `factor` フィールドに格納されており、数値との高速な乗算を可能にします。

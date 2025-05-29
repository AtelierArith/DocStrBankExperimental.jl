`getx()` は `SimplePolynomial(0,1)` を作成する便利な方法です。典型的な使用法：

```
x = getx()
p = 2 + x - 3*x^2
```

係数の型 `T` のためには `getx(T)` を使用します。例えば、`getx(Mod{13})` のように。

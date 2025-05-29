```
expand(expr)
```

式を展開して、乗法を加算に分配します。たとえば、`a*(b+c)` は `ab+ac` になります。

`expand` は、置換シンボルと非代数式を `variable_type` 型の変数に置き換えて、専門のスパース多変数多項式実装を使用して分配を計算します。`variable_type` は `MultivariatePolynomials.AbstractVariable` の任意のサブタイプであることができます。

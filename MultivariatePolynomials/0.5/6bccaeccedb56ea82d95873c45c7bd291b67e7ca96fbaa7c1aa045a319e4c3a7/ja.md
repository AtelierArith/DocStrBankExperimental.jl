```
@similar_variable(p::AbstractPolynomialLike, variable)
```

`similar_variable(p, Val{variable})`を呼び出し、その結果を同じ名前の変数にバインドします。

### 例

`TypedPolynomials`で作成された多項式に対して`@similar_variable typedpoly x`を呼び出すと、`TypedPolynomials.Variable{:x}`が変数`x`にバインドされます。

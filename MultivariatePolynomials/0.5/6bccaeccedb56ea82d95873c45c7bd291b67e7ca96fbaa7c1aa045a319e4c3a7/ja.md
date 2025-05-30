```
@similar_variable(p::AbstractPolynomialLike, variable)
```

`similar_variable(p, Val{variable})`を呼び出し、結果を同じ名前の変数にバインドします。

### 例

`@similar_variable typedpoly x`を`TypedPolynomials`で作成した多項式に対して呼び出すと、`TypedPolynomials.Variable{:x}`が変数`x`にバインドされます。

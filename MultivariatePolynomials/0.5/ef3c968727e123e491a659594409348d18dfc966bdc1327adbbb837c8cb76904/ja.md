```
similar_variable(p::AbstractPolynomialLike, variable::Type{Val{V}})
```

与えられたソース多項式に基づいて新しい変数 `V` を作成します。

```
similar_variable(p::AbstractPolynomialLike, v::Symbol)
```

与えられたソース多項式と与えられたシンボル `v` に基づいて新しい変数を作成します。これは型の不安定性を引き起こす可能性があることに注意してください。

### 例

`TypedPolynomials` で作成された多項式に対して `similar_variable(typedpoly, Val{:x})` を呼び出すと、`TypedPolynomials.Variable{:x}` になります。

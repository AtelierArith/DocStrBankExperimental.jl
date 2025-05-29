```
ComposableExpression{T,N,D} <: AbstractComposableExpression{T,N} <: AbstractExpression{T,N}
```

数式を式木（`tree::N`）として表現する象徴的表現で、関連するメタデータ（`metadata::Metadata{D}`）を持ちます。象徴的回帰タスクにおいて式を構築し操作するために使用されます。

例：

変数 `x1` と `x2` を作成し、式 `f = x1 * sin(x2)` を構築します：

```julia
operators = OperatorEnum(; binary_operators=(+, *, /, -), unary_operators=(sin, cos))
variable_names = ["x1", "x2"]
x1 = ComposableExpression(Node(Float64; feature=1); operators, variable_names)
x2 = ComposableExpression(Node(Float64; feature=2); operators, variable_names)
f = x1 * sin(x2)
# ^これは、渡されたものの最初と二番目の引数を参照します：

f(x1, x1) # == x1 * sin(x1)
f(randn(5), randn(5)) # == randn(5) .* sin.(randn(5))

# それを自分自身に渡すこともできます：
f(f, f) # == (x1 * sin(x2)) * sin((x1 * sin(x2)))
```

```
variables(expr::Expression; parameters = Variable[])
variables(exprs::AbstractVector{Expression}; parameters = Variable[])
```

与えられた式で使用されているすべての変数を、`parameters` で宣言されたものまで取得します。

## 例

```julia-repl
julia> @var x y a;
julia> variables(x^2 + y)
2-element Array{Variable,1}:
 x
 y

julia> variables([x^2 + a, y]; parameters = [a])
2-element Array{Variable,1}:
 x
 y
```

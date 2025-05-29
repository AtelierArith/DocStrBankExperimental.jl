```
evaluate(expr::Expression, subs...)
evaluate(expr::AbstractArray{Expression}, subs...)
```

与えられた式を評価します。

## 例

```julia-repl
julia> @var x y;

julia> evaluate(x^2, x => 2)
4

julia> evaluate(x * y, [x,y] => [2, 3])
6

julia> evaluate([x^2, x * y], [x,y] => [2, 3])
2-element Array{Int64,1}:
 4
 6

# 呼び出し可能な構文を使用することもできます
julia> [x^2, x * y]([x,y] => [2, 3])
2-element Array{Int64,1}:
 4
 6
```

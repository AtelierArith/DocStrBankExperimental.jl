```
subs(expr::Expression, subsitutions::Pair...)
subs(exprs::AbstractVector{<:Expression}, subsitutions::Pair...)
```

与えられた式に対して、指定された置換を適用します。

## 例

```julia-repl
@var x y

julia> subs(x^2, x => y)
y ^ 2

julia> subs(x * y, [x,y] => [x+2,y+2])
(x + 2) * (y + 2)

julia> subs([x + y, x^2], x => y + 2, y => x + 2)
2-element Array{Expression,1}:
 4 + x + y
 (2 + y)^2

# 呼び出し可能な構文を使用することもできます
julia> (x * y)([x,y] => [x+2,y+2])
 (x + 2) * (y + 2)
```

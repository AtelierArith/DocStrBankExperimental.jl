```
rewrite_generator(expr::Expr, inner::Function)
```

生成子文を `expr` として書き換え、指定されたネストされたフィルタを持つ適切にネストされた for ループを返します。

# 例

```jldoctest
julia> using MutableArithmetics

julia> MutableArithmetics.rewrite_generator(:(i for i in 1:2 if isodd(i)), i -> :($i + 1))
:(for $(Expr(:escape, :(i = 1:2)))
      if $(Expr(:escape, :(isodd(i))))
          i + 1
      end
  end)
```

```
expr_map(f, c...; skip_nothing::Bool=false)
```

`Base.map`に似ていますが、`f`が式を返すことを期待し、これらの式を`Expr(:block, ...)`式として連結します。

`skip_nothing`が`true`の場合は`nothing`をスキップします。

# 例

```jldoctest
julia> expr_map(1:10, 2:11) do i,j
           :(1 + $i + $j)
       end
quote
    1 + 1 + 2
    1 + 2 + 3
    1 + 3 + 4
    1 + 4 + 5
    1 + 5 + 6
    1 + 6 + 7
    1 + 7 + 8
    1 + 8 + 9
    1 + 9 + 10
    1 + 10 + 11
end
```

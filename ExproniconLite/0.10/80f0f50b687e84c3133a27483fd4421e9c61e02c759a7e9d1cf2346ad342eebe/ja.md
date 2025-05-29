```
nexprs(f, n::Int)
```

`f`を評価することによって`n`個の類似の式を作成します。

# 例

```jldoctest
julia> nexprs(5) do k
           :(1 + $k)
       end
quote
    1 + 1
    1 + 2
    1 + 3
    1 + 4
    1 + 5
end
```

```
..(a, b)
```

a と b の間の区間を定義します（両端を含む）。

# 例

```julia-repl
julia> my_interval = (-π..π)

julia> rand(my_interval, 5)
5-element Vector{Float64}:
 0.5111482297554093
 1.1984728844571544
 1.3279941255812906
 2.3429444282250502
 3.0495310142685526
```

関連項目 [`BoxConstrainedSpace`](@ref)

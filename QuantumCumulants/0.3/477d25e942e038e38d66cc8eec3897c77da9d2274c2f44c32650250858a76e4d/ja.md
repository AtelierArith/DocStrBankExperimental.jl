```
get_order(arg)
```

与えられた引数の順序を計算します。これは、何かを[`cumulant_expansion`](@ref)メソッドを使用して展開すべきかどうかを決定するために使用される順序です。

# 例

```
julia> get_order(a)
1

julia> get_order(a*b)
2

julia> get_order(1)
0
```

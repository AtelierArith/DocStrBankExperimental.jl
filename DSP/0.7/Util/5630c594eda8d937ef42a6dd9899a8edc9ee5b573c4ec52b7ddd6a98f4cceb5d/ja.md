```
alignsignals(x, y)
```

finddelay() と shiftsignal() を使用して x を y に時間的に整列させます。また、y に対する x の遅延も返します。

# 例

```jldoctest
julia> alignsignals([0, 0, 1, 2, 3], [1, 2, 3])
([1, 2, 3, 0, 0], 2)

julia> alignsignals([1, 2, 3], [0, 0, 1, 2, 3])
([0, 0, 1], -2)
```

詳細は [`alignsignals!`](@ref) を参照してください。

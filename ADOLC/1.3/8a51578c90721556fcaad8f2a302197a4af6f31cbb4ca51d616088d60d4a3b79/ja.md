```
partial_to_adolc_format(partial::Vector{I_1}, degree::I_2) where {I_1<:Integer, I_2<:Integer}
```

与えられた `partial` を [ADOLC-Format](@ref) に変換します。

!!! note
    `partial` は `Partial-format` である必要があります。


# 例:

```jldoctest

partial = [1, 0, 4]
degree = sum(partial)
partial_to_adolc_format(partial, degree)

# 出力

5-element Vector{Int32}:
 3
 3
 3
 3
 1
```

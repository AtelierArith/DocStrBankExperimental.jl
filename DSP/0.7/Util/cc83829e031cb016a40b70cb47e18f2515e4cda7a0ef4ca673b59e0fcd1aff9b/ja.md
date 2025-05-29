```
shiftsignal(x, s)
```

信号 x の要素を指定されたサンプル数 s だけ時間的にシフトし、空いたスペースをゼロで埋めます。円形シフトを行うには、circshift を使用してください。

# 例

```jldoctest
julia> shiftsignal([1, 2, 3], 2)
3-element Vector{Int64}:
 0
 0
 1

julia> shiftsignal([1, 2, 3], -2)
3-element Vector{Int64}:
 3
 0
 0
```

他にも [`shiftsignal!`](@ref) を参照してください。

```
w = width(iv)
```

区間 `iv` の幅 (最大値 - 最小値) を計算します。整数 `l` と `r` に対して、`width(l..r) = length(l:r) - 1` であることに注意してください。

# 例

```jldoctest
julia> width(2..7)
5

julia> length(2:7)
6
```

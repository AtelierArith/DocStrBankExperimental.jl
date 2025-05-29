```
levicivita(p)
```

順列 `p` のレヴィ＝チヴィタ記号を計算します。順列が偶数の場合は 1 を、奇数の場合は -1 を、それ以外の場合は 0 を返します。

順列が奇数であるのは、偶数長のサイクルの数が奇数である場合に限るという事実を用いて、パリティが計算されます。

# 例

```jldoctest
julia> levicivita([1, 2, 3])
1

julia> levicivita([3, 2, 1])
-1

julia> levicivita([1, 1, 1])
0

julia> levicivita(collect(1:100))
1

julia> levicivita(ones(Int, 100))
0
```

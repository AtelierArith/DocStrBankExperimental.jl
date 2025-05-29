```
selectsizes(x::AbstractArray, dim; keep_dims=true)
```

複数の次元のサイズに1回の呼び出しでアクセスするための追加のサイズメソッドです。`keep_dims`を使用すると、他の次元をシングルトンとして返すことができます。

# 例

```jldoctest
julia> x = ones((2,4,6,8, 10));

julia> selectsizes(x, (2,3))
(1, 4, 6, 1, 1)

julia> selectsizes(x, 5)
(1, 1, 1, 1, 10)

julia> selectsizes(x, (5,))
(1, 1, 1, 1, 10)

julia> selectsizes(x, (2,3,4), keep_dims=false)
(4, 6, 8)

julia> selectsizes(x, (4,3,2), keep_dims=false)
(8, 6, 4)
```

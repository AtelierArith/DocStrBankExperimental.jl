```julia
datalength(buf)

```

`buf`に保持できるデータの最大数を返します。

# 例

```jldoctest
julia> buf = Buffer(5);

julia> datalength(buf)
5

julia> buf2 = Buffer(2, 10);

julia> datalength(buf2)
10
```

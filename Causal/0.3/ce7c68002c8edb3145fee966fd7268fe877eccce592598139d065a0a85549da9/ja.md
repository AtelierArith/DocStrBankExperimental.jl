```julia
ishit(buf)

```

`buf` のインデックスが `buf` のデータ長の整数倍である場合に true を返します。

# 例

```jldoctest
julia> buf = Buffer(3);

julia> for val in 1 : 7
       write!(buf, val)
       @show ishit(buf)
       end
ishit(buf) = false
ishit(buf) = false
ishit(buf) = true
ishit(buf) = false
ishit(buf) = false
ishit(buf) = true
ishit(buf) = false
```

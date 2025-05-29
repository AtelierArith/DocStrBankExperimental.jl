```julia
nearest(T, x)
```

`x`を型Tで表現可能な最も近い値に変換し、不正確な場合は丸めます。

### 例

```julia julia> nearest(Int, 1234.56) 1235

julia> nearest(Int, Inf) 9223372036854775807

julia> nearest(Int, -Inf) -9223372036854775808 ````

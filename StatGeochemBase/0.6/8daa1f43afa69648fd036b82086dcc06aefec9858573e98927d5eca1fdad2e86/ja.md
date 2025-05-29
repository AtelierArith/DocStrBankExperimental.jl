```julia
sigdigits(d)
```

数値 `d` の小数点以下の有効数字の桁数を決定します。

### 例

```julia
julia> sigdigits(1000)
1

julia> sigdigits(1001)
4

julia> sigdigits(1001.1245)
8
```

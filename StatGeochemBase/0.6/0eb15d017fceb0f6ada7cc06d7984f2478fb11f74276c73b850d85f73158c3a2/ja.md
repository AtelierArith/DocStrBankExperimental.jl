```julia
leastsigfig(d)
```

数 `d` の最も重要でない小数桁の桁数を返します。

### 例

```julia
julia> leastsigfig(1000)
1000.0

julia> leastsigfig(1001)
1.0

julia> leastsigfig(1001.1234)
0.0001
```

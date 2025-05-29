```
inradians([Type],x)
```

与えられた角度の値を、Type（デフォルトはFloat64）でラジアンに変換します。単位のない数値はラジアンであると見なされ、静かに通過します。

## 例

```jldoctest
julia> inradians(180°)
3.141592653589793

julia> inradians(2π)
6.283185307179586

julia> inradians(0.5π*rad)
1.5707963267948966
```

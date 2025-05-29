```
regularize!(f::Vector{T} [; k=3]) where T<:Real
```

原点に非解析点を持つ関数の正則化。

#### 例:

```
julia> r = [0,1,2,3,4,5];

julia> f = r ./ r; println(f)
[NaN, 1.0, 1.0, 1.0, 1.0, 1.0]

julia> regularize!(f); ; println(f)
[1.0, 1.0, 1.0, 1.0, 1.0, 1.0]
```

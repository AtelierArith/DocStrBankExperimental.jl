```
Scaler(k, b)
```

線形変換 `y = k x + b` を作成します。

`k` がゼロの場合は `ArgumentError` をスローします。

# 例

```jldoctest
julia> Scaler(2.0, 1)
y = 2.0 x + 1

julia> Scaler(-1, 1.4)
y = -x + 1.4

julia> Scaler(1.0, 2)
y = x + 2

julia> Scaler(1, 2)
y = x + 2

julia> Scaler(1, 2).(1:4)
4-element Vector{Int64}:
 3
 4
 5
 6

julia> Scaler(1, 2)(I)
UniformScaling{Int64}
3*I
```

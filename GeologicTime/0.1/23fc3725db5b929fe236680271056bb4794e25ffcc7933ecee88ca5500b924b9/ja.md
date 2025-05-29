```
getspan(name::AbstractString) :: NTuple{2, Float64}
```

地質時代の時間範囲（両端は百万年単位）を見つけます。

# 例

```jldoctest
julia> getspan("Jurassic")
(201.4, 145.0)
```

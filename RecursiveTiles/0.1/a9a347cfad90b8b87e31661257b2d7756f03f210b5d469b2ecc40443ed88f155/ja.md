```
findranges(f, A::AbstractArray)
```

`isequal(f(A[i]), f(A[i+δ]))` が真である `eachindex(A)` 上の各範囲を見つけます。最初の範囲は `i=firstindex(A)` から始まり、次の範囲は `i=i+δⱼ+1` から始まります。ここで `δⱼ` は前の範囲の終了と開始の差です。

# 例

```jldoctest
julia> findranges(signbit, -5:5)
2-element Vector{UnitRange{Int64}}:
 1:5
 6:11

julia> findranges(identity, [0, missing, missing, 1, 1])
3-element Vector{UnitRange{Int64}}:
 1:1
 2:3
 4:5
```

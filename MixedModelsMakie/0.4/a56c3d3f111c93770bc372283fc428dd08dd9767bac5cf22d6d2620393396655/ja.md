```
splomaxes!(f::Indexable, labels::AbstractVector{<:AbstractString},
           panel!::Function, args...;
           extraticks::Bool=false, kwargs...)
```

`labels`のすべてのペアに対して、下三角に`(k*(k-1))/2`の軸のセットで`f`を埋めます。ここで、`k`は`labels`の長さです。`panel!`関数は、`panel!(ax::Axis, i::Integer, j::Integer, args...; kwargs...)`というシグネチャを持ち、`ax`内の[i,j]パネルを描画する必要があります。

```
Materials(
    name::AbstractString,
    els::AbstractArray{Element},
    ::Type{U},
    dims::Tuple;
    atomicweights::AbstractDict{Element,V} = Dict{Element,Float64}(),
    properties::AbstractDict{Symbol,Any} = Dict{Symbol,Any}(),
) where {U<:AbstractFloat, V<:AbstractFloat}
```

複数のポイントの組成を表す型で、`KRatios`および`HyperSpectrum`の補完として機能します。データは`Array{Material}`よりもはるかにメモリ効率の良い方法で保存されますが、座標によって`mats[1,2]`のようにアクセスして`Material`を返したり、元素によって`mats[n"Fe"]`のようにアクセスして質量分率の値の配列を返したりすることができます。

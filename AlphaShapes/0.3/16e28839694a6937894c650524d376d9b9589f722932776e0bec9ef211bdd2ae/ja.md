```
AlphaShape(X::AbstractArray{Float64,2};α::Union{Nothing,Float64}=nothing,
    search::Tuple{Float64,Float64}=(0.0, 10.0),
    MaxSteps::Int=100)::AbstractArray{Float64,3}
```

2DのAbstractArrayの点X: [2,npoints]に対応するアルファシェイプを見つけます。そして、α値αを使用します。

もしα == nothingであれば、最適な値を見つけるためにsearchの範囲での探索が行われます。最適化の目的は、すべての点Xがアルファシェイプの三角形分割に含まれることを条件として、アルファシェイプの面積を最小化することです。

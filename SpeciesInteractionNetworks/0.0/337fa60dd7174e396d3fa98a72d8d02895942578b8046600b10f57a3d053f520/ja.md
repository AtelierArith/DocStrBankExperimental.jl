```
nodf(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: Union{BipartiteNetwork,BipartiteQuantitativeNetwork}}
```

ネットワークのマージンに対する `nodf` を返します。`i` 引数は、トップレベルの場合は 1、ボトムレベルの場合は 2 であり、無効な値が使用された場合は `ArgumentError` がスローされます。定量的ネットワークの場合は、*WNODF* が使用されます。

###### 参考文献

[AlmeidaNeto2008consistent](@citet*)

[AlmeidaNeto2011straightforward](@citet*)

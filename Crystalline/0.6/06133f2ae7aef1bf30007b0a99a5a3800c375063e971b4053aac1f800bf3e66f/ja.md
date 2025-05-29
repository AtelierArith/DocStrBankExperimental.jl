```
Collection{T} <: AbstractVector{T}
```

`Vector{T}`のラッパーで、カスタム印刷およびカスタム`T`（例：`AbstractIrrep` & `NewBandRep`）のディスパッチルールを許可します。

Crystallineでは、ラップされたベクターのすべての要素が*同じ*空間、点、または小群に関連付けられていると仮定されています。したがって、`T`が[`dim`](@ref)または[`num`](@ref)を実装している場合、いずれも`Collection`の各要素に対して同じ値を返さなければならず（`dim(::Collection)`および`num(::Collection)`に等しい）、なければなりません。

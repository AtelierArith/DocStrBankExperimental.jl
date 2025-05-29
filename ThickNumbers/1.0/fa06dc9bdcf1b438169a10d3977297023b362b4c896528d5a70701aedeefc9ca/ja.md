```
emptyset(::Type{TN}) where TN<:ThickNumber
emptyset(x::ThickNumber)
```

タイプ `TN` の「空集合」を構築します。

# デフォルト実装

デフォルト実装は、`loval` が `hival` より大きくなることによって空集合を作成します。具体的には、デフォルト実装は次のようになります。

```
emptyset(::Type{TN}) where TN<:ThickNumber{T} where T = lohi(TN, typemax(T), typemin(T))
```

# 例

```julia
julia> emptyset(Interval{Float64})
Interval{Float64}(Inf, -Inf)
```

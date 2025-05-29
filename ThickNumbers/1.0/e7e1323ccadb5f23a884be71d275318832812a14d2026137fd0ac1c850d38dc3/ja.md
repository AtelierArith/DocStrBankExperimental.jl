```
basetype(::Type{TN}) where TN<:ThickNumber
```

`valuetype`を`TN`から削除します。

# インターフェース要件

`basetype`はすべてのThickNumberサブタイプによって実装されなければなりません。

# 例

`Interval`を実装するパッケージでは、次のように定義します。

```julia
ThickNumbers.basetype(::Type{Interval{T}}) where T = Interval
ThickNumbers.basetype(::Type{Interval}) = Interval
```

これにより、

```julia
julia> basetype(Interval{Float64})
Interval
```

のように使用できます。これを使用して、`valuetype`に依存しないThickNumbersを構築できます。

```julia
julia> lohi(basetype(Interval{Float64}), 1, 2))
Interval{Int64}(1, 2)
```

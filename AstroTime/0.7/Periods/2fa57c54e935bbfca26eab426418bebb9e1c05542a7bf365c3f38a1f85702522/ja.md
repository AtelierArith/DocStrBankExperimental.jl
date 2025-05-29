```
AstroPeriod{U, T}(unit, Δt) where {U<:TimeUnit, T}
```

`AstroPeriod`オブジェクトは、`Δt`の時間間隔を`unit`の[`TimeUnit`](@ref)で表します。期間は、以下の例に示す短縮構文を使用して構築する必要があります。

### 例

```jldoctest; setup = :(using AstroTime)
julia> 3.0seconds
3.0 seconds

julia> 1.0minutes
1.0 minutes

julia> 12hours
12.0 hours

julia> days_per_year = 365
365
julia> days_per_year * days
365.0 days

julia> 10.0years
10.0 years

julia> 1centuries
1.0 centuries
```

```
temporalranges(A::ClimArray, f = Dates.month) → r
temporalranges(t::AbstractVector{<:TimeType}}, f = Dates.month) → r
```

同じ月、年、日、または季節に属する`t`の値のインデックスの範囲を返すベクトルを返します。`f`は次の値を取ることができます: `Dates.year, Dates.month, Dates.day`または`season`（すべて関数です）。

例えば、[`monthlyagg`](@ref)、[`yearlyagg`](@ref)または[`seasonalyagg`](@ref)で使用されます。

```
@u_str(unit)
```

単位、次元、または[`Unitful.register`](@ref)で登録された単位モジュールで定義された量を簡単に呼び出すための文字列マクロです。

異なるモジュールで定義された[`Unitful.Units`](@ref)オブジェクトに同じシンボルが使用されている場合、最も最近登録されたモジュールで見つかったシンボルが使用されます。

内部に入るものは、有効なJulia式として解析可能でなければなりません。言い換えれば、`u"N m"`は`u"N*m"`を書くつもりだった場合、失敗します。

例:

```jldoctest
julia> 1.0u"m/s"
1.0 m s^-1

julia> 1.0u"N*m"
1.0 m N

julia> u"m,kg,s"
(m, kg, s)

julia> typeof(1.0u"m/s")
Quantity{Float64, 𝐋 𝐓^-1, Unitful.FreeUnits{(m, s^-1), 𝐋 𝐓^-1, nothing}}

julia> u"ħ"
1.0545718176461565e-34 J s
```

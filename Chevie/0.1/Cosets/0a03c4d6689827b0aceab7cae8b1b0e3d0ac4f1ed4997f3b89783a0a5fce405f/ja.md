spets(s::String) はいくつかの例外的な spets を構築します

```julia-repl
julia> spets("3G422")
³G₄‚₂‚₂

julia> spets("2G5")
²G(ζ₃²√-2)₅

julia> spets("3G333")
G₃‚₃‚₃₍₁‚₂‚₃‚₄₄₎=³G₃‚₃‚₃₍₁‚₂‚₃‚₄₄₎

julia> spets("3pG333")
G₃‚₃‚₃₍₁‚₂‚₃‚₄₄₎=³G₃‚₃‚₃₍₁‚₂‚₃‚₄₄₎

julia> spets("4G333")
G₃‚₃‚₃₍₂‚₁₂‚₁₁‚₁₆‚₅₃‚₁₀‚₄₃‚₃₆₎=⁴G₃‚₃‚₃₍₁‚₂‚₃‚₃₂‚₁₆‚₃₆‚₃₀‚₁₀₎
```

```
    LabelNumeral{T <: Integer}(::T; prefix="", caselower=false)
    LabelNumeral{T <: Integer}(::Type{T}, i::Integer; prefix="", caselower=false)
    LabelNumeral{T <: Integer}(::Type{T}, s::String; prefix="", caselower=false)
```

例:

```
julia> using RomanNumerals

julia> a = LabelNumeral(rn"XXIV"; prefix="A-", caselower=true)
A-xxiv

julia> a = LabelNumeral(rn"XXIV"; prefix="A-")
A-XXIV
```

LabelNumeralのコンストラクタ

```
struct FunctionalCondition{FT<:AbstractFeature} <: AbstractCondition{FT}
    feature::FT
    f::FT
end
```

関数の値に等しい真理値を返す条件。

関連項目として [`AbstractFeature`](@ref) を参照してください。

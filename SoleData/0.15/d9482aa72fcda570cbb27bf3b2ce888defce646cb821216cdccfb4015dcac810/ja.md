```
struct ValueCondition{FT<:AbstractFeature} <: AbstractCondition{FT}
    feature::FT
end
```

特徴の値に等しい真理値を返す条件です。

関連情報は[`AbstractFeature`](@ref)を参照してください。

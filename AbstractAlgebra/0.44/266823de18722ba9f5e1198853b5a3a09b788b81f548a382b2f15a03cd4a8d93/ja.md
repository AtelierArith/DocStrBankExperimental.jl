```
echelon_form_with_transformation(A::MatElem{<:FieldElement}; reduced::Bool = true, shape::Symbol = :upper)
```

行基本形 $R$ と $R = UA$ を満たす可逆行列 $U$ を返します。

キーワード引数については [`echelon_form`](@ref) を参照してください。

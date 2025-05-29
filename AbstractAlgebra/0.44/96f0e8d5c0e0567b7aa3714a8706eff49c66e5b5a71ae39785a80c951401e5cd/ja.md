```
hermite_form_with_transformation(A::MatElem{<:RingElement}; reduced::Bool = true, shape::Symbol = :upper)
```

行列 $A$ のエルミート標準形 $H$ と、$H = UA$ となる可逆行列 $U$ を返します。`base_ring(A)` がユークリッドであると仮定します。

キーワード引数については [`hermite_form`](@ref) を参照してください。

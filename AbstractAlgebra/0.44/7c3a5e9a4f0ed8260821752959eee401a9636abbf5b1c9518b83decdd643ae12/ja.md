```
howell_form_with_transformation(A::MatElem{<:RingElement}; reduced::Bool = true, shape::Symbol = :upper)
```

行列 $A$ のハウエル形式 $H$ と $H = UA$ を満たす行列 $U$ を返します。$H$ は $A$ よりも行が多い場合があり、そのため $U$ は可逆でない可能性があります。`base_ring(A)` が主イデアル環であると仮定します。

キーワード引数については [`hermite_form`](@ref) を参照してください。

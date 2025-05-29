```
hermitian_genera(E::NumField, rank::Int,
                              signatures::Dict{InfPlc, Int},
                              determinant::Union{Hecke.RelNumFieldOrderIdeal, Hecke.RelNumFieldOrderFractionalIdeal};
                              min_scale::Union{Hecke.RelNumFieldOrderIdeal, Hecke.RelNumFieldOrderFractionalIdeal} = is_integral(determinant) ? inv(1*order(determinant)) : determinant,
                              max_scale::Union{Hecke.RelNumFieldOrderIdeal, Hecke.RelNumFieldOrderFractionalIdeal} = is_integral(determinant) ? determinant : inv(1*order(determinant)))
                                                                                                             -> Vector{HermGenus}
```

代数`E`上のエルミート格子のすべてのグローバル属符号を返します。ランクは`rank`、署名は`signatures`で与えられ、スケールは`max_scale`で制限され、行列式クラスは`determinant`に等しいです。

`max_scale == nothing`の場合、それは`determinant`に等しく設定されます。

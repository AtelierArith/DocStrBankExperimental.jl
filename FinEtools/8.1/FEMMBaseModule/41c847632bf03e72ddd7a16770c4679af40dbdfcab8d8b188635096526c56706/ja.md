```
field_elem_to_nodal!(
    self::AbstractFEMM,
    geom::NodalField{FT},
    ef::EFL,
    nf::NFL;
    kind = :weighted_average,
) where {FT, T<:Number, EFL<:ElementalField{T}, NFL<:NodalField{T}}
```

要素場から離散多様体上のノーダル場を作成します。

`ef` = 値を供給する要素場 `nf` = 値を受け取るノーダル場 `kind` = デフォルトは `:weighted_average`；他のオプション： `:max`

`nf` を返します。

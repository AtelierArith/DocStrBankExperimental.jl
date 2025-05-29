```
field_nodal_to_elem!(
    self::AbstractFEMM,
    geom::NodalField{FT},
    nf::NFL,
    ef::EFL;
    kind = :weighted_average,
) where {FT<:Number, T, EFL<:ElementalField{T}, NFL<:NodalField{T}}
```

離散多様体上のノーダルフィールドからエレメンタルフィールドを作成します。

`nf` = 値を供給するノーダルフィールド `ef` = 値を受け取るエレメンタルフィールド `kind` = デフォルトは `:weighted_average`；他のオプション： `:max`

`ef` を返します。

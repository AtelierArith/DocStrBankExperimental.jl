```
η(::Type{<:BackscatterCoefficient}, mat::Material, e0::Float64) = #
η(elm::Element, e0::Real)
```

モデルは次のとおりです: Tomlin1963, LoveScott1978η, Pouchou1991η, August1989η, Reimer1998

デフォルトのバックスキャッター係数アルゴリズムはAugust1989ηです。

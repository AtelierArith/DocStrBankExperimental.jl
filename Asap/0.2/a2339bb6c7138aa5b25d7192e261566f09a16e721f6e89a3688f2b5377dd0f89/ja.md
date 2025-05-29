```
GravityLoad(element::Element, factor::Float64)
```

メンバーに沿って適用される重力荷重（負のグローバルZ）。

分布荷重 w = element.section.A * element.section.ρ * factor を生成します。ここで、factor は重力による適切な加速度である必要があります。

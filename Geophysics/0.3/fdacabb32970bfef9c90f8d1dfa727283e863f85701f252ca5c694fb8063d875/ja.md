```
thermaldiffusivity(h::Real=0,W::Weather=Standard) = thermaldiffusivity(W(h))
```

気温の拡散率 `α` は、`Weather` の位置の高度 `h` での値 (m²⋅s⁻¹ または ft²⋅s⁻¹)。

```
specificvolume(h::Real=0,W::Weather=Standard) = specificvolume(W(h))
```

特定体積 `v` は、`Weather` の位置の高度 `h` での質量あたり (m³⋅kg⁻¹, ft³⋅slug⁻¹)。

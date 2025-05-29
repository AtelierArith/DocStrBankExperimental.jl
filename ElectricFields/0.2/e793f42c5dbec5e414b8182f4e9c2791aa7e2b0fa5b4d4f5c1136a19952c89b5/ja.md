```
field_amplitude_spectrum(f::AbstractField, ω)
```

フィールド `f` の [`field_amplitude`](@ref) の解析フーリエ変換を角周波数 `ω` で計算します。フーリエの恒等式を使用します。

$$
\vec{F}(t) = -\partial_t \vec{A}(t)
\iff
\hat{\vec{F}}(\omega) = -\im\omega \hat{\vec{A}}(\omega)
$$

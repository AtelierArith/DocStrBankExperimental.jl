See also: [`DiscreteImpulse`](@ref), [`frequency_to_time`](@ref)

```
ContinuousImpulse{T<:AbstractFloat}
```

解析インパルス関数を表すために使用される構造体です。2つのフィールドを持ちます：`in_time` は時間 `t` の関数であり、`in_freq` は角周波数 `ω` の関数です。`in_freq` は `in_time` のフーリエ変換であるべきですが、これは強制されません。

フーリエ変換の定義を使用します：F(ω) =  ∫ f(t)*exp(im*ω*t) dt, f(t) = (2π)^(-1) * ∫ F(ω)*exp(-im*ω*t) dω。

インパルス f(t) はフィールド u(t) と時間的に畳み込まれますが、インパルス f(t) のフーリエ変換 F(ω) を使用することで畳み込みを回避します。これにより次のようになります。

周波数から時間への変換: (2π)^(-1) * ∫ F(ω)*U(ω)*exp(-im*ω*t) dω

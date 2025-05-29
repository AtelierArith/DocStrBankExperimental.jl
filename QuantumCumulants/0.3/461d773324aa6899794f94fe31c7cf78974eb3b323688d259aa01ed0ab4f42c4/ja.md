```
struct Spectrum
```

スペクトルを表す型、すなわち定常状態における[`CorrelationFunction`](@ref)のフーリエ変換です。

実際に周波数`ω`でスペクトルを計算するには、相関関数の上に型を構築し、`Spectrum(c)(ω,usteady,p0)`を呼び出します。

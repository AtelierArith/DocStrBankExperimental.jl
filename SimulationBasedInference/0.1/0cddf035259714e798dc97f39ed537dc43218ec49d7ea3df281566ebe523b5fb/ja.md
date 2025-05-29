```
unconstrained_forward_map(prior::AbstractSimulatorPrior, ζ)
```

制約のない空間から前方モデルパラメータ `(g ∘ f): Ζ ↦ Θ ↦ Φ` への前方写像を適用します。ここで `f⁻¹` は `prior` の逆双射（すなわち、制約のない Ζ から制約のある Θ 空間への写像）であり、`g` は Θ から前方モデルのパラメータ空間 Φ への写像を定義する `forward_map` によって定義されます。

```
envelope(pulsed_field::AbstractPulsedPlaneWaveField, phi::Real)
```

与えられた `pulsed_field` と位相 `phi` に対する位相エンベロープ関数（パルスエンベロープまたはパルス形状とも呼ばれる）の値を返します。`phi` のドメインチェックを行った後、[`_envelope`](@ref) を呼び出します。`phi` が `[domain](@ref)` によって返されるドメインにない場合はゼロを返します。

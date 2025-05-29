```
polarization_vector(pol::AbstractPolarization, mom::QEDbase.AbstractFourMomentum)
```

与えられた偏光と四モーメント `mom` に対する偏光ベクトルを返します。特定の偏光の場合、対応する `LorentzVector` が返されますが、未定義の偏光の場合は偏光ベクトルのタプルが返されます。

!!! note "慣習"
    現在の実装では、`QEDcore.jl` によって提供される `Photon` の `base_state` 関数を使用しています。


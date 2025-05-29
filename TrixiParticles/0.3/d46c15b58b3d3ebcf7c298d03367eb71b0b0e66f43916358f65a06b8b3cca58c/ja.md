```
TransportVelocityAdami(background_pressure::Real)
```

輸送速度定式 (TVF) は、ペアリングと引張不安定性を抑制するためのものです。手法の詳細については、[TVF](@ref transport_velocity_formulation)を参照してください。

# 引数

  * `background_pressure`: 背景圧力。推奨される背景圧力は、基準圧力のオーダーであることです。

!!! note
    `TransportVelocityAdami`を使用する際には、引張不安定性を抑制するために人工粘性を必要としません。したがって、[`ViscosityAdami`](@ref)を粘性モデルとして使用することを強く推奨します。[`ArtificialViscosityMonaghan`](@ref)は悪い結果をもたらすためです。


```
Buffer(device::T, samples_count, cyclic::Bool = false) where {T <: AbstractDeviceOrTrigger}
```

新しい Buffer インスタンスを初期化します。

# パラメータ

  * `device::AbstractDeviceOrTrigger` : バッファが属するデバイスインスタンス（[`Device`](@ref) または [`Trigger`](@ref) のいずれか）
  * `samples_count` : バッファのサイズ（サンプル数）
  * `cyclic` : true に設定されている場合、バッファは円形です

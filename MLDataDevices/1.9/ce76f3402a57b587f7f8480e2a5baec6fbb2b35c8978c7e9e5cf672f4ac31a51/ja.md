```
get_device_type(x) -> Type{<:AbstractDevice} | Exception | Type{Nothing}
```

[`get_device`](@ref)と似ていますが、デバイス自体ではなくデバイスタイプを返します。この値はしばしばコンパイル時定数であり、デバイスタイプに基づいてディスパッチを定義する際には[`get_device`](@ref)の代わりに使用することが推奨されます。

!!! note
    正しいデバイスを返すためには、Trigger Packagesをロードする必要があります。


## 特殊な返される値

  * `Nothing` – オブジェクトがデバイスに依存しないことを示します。例えば、スカラー、抽象範囲などです。
  * `UnknownDevice` – デバイスタイプが不明であることを示します。

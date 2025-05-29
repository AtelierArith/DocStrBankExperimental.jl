フラグタイプ `name` の仕様で、これは `typealias` の型エイリアスです。ビットマスク構造体に関連付けることができ、その場合 `bitmask` 番号は対応する `SpecBitmask` に設定されます。

```julia
struct SpecFlag <: VulkanSpec.Spec
```

  * `name::Symbol`: フラグタイプの名前。
  * `typealias::Symbol`: エイリアスする型。
  * `bitmask::Union{Nothing, VulkanSpec.SpecBitmask}`: ビットマスク（該当する場合）。

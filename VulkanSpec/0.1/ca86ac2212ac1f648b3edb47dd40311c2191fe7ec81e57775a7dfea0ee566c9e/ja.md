ビットマスク型の仕様であり、`bits`の組み合わせを通じて形成される必要があります。

通常、意味を持つビットを持つ`UInt32`型のエイリアスです。

```julia
struct SpecBitmask <: VulkanSpec.Spec
```

  * `name::Symbol`: ビットマスク型の名前。
  * `bits::StructArrays.StructVector{VulkanSpec.SpecBit}`: 最終的なビットマスク値を形成するために組み合わせることができる有効なビット。
  * `combinations::StructArrays.StructVector{VulkanSpec.SpecBitCombination}`
  * `width::Integer`

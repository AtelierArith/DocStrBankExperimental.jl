列挙型の仕様。

```julia
struct SpecEnum <: VulkanSpec.Spec
```

  * `name::Symbol`: 列挙型の名前。
  * `enums::StructArrays.StructVector{VulkanSpec.SpecConstant}`: 可能な列挙値のベクター。

ビットマスクで使用されるビットの仕様。

```julia
struct SpecBit <: VulkanSpec.Spec
```

  * `name::Symbol`: ビットの名前。
  * `position::Int64`: ビットの位置。

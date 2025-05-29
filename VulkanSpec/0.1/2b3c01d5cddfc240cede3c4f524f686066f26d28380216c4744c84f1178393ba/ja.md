定数の仕様。

```julia
struct SpecConstant <: VulkanSpec.Spec
```

  * `name::Symbol`: 定数の名前。
  * `value::Any`: 定数の値。

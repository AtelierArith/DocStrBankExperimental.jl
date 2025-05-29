Function `func` that creates a `handle` from a create info structure `create_info_struct` passed as the value of the parameter `create_info_param`.

If `batch` is true, then `func` expects a list of multiple create info structures and will create multiple handles at once.

```julia
struct CreateFunc <: VulkanSpec.Spec
```

  * `func::VulkanSpec.SpecFunc`
  * `handle::VulkanSpec.SpecHandle`
  * `create_info_struct::Union{Nothing, VulkanSpec.SpecStruct}`
  * `create_info_param::Union{Nothing, VulkanSpec.SpecFuncParam}`
  * `batch::Bool`

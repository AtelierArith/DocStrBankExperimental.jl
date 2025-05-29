Function `func` that destroys a `handle` passed as the value of the parameter `destroyed_param`.

If `batch` is true, then `func` expects a list of multiple handles and will destroy all of them at once.

```julia
struct DestroyFunc <: VulkanSpec.Spec
```

  * `func::VulkanSpec.SpecFunc`
  * `handle::VulkanSpec.SpecHandle`
  * `destroyed_param::VulkanSpec.SpecFuncParam`
  * `batch::Bool`

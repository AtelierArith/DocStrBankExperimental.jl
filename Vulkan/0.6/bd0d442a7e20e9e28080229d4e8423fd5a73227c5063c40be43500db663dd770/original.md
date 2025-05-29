High-level wrapper for VkInstanceCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkInstanceCreateInfo.html)

```julia
struct InstanceCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.InstanceCreateFlag`
  * `application_info::Union{Ptr{Nothing}, Vulkan.ApplicationInfo}`
  * `enabled_layer_names::Vector{String}`
  * `enabled_extension_names::Vector{String}`

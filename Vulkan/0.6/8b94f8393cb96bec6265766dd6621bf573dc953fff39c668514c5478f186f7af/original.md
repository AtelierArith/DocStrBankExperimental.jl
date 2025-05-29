High-level wrapper for VkCommandPoolCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandPoolCreateInfo.html)

```julia
struct CommandPoolCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.CommandPoolCreateFlag`
  * `queue_family_index::UInt32`

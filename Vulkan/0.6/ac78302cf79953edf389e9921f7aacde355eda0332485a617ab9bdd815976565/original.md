Arguments:

  * `create_info::_BufferCreateInfo`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceBufferMemoryRequirements.html)

```julia
_DeviceBufferMemoryRequirements(
    create_info::Vulkan._BufferCreateInfo;
    next
) -> Vulkan._DeviceBufferMemoryRequirements

```

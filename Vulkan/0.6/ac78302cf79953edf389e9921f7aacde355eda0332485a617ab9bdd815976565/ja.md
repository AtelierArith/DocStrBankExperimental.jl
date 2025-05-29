引数:

  * `create_info::_BufferCreateInfo`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceBufferMemoryRequirements.html)

```julia
_DeviceBufferMemoryRequirements(
    create_info::Vulkan._BufferCreateInfo;
    next
) -> Vulkan._DeviceBufferMemoryRequirements

```

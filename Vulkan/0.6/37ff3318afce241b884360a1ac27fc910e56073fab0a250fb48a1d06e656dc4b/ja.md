拡張: VK*NV*device*generated*commands

戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::_IndirectCommandsLayoutCreateInfoNV`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateIndirectCommandsLayoutNV.html)

```julia
_create_indirect_commands_layout_nv(
    device,
    create_info::Vulkan._IndirectCommandsLayoutCreateInfoNV;
    allocator
) -> ResultTypes.Result{Vulkan.IndirectCommandsLayoutNV, Vulkan.VulkanError}

```

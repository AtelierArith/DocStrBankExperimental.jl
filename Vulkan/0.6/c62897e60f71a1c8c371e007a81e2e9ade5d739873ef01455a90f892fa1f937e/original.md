Extension: VK_NV_device_generated_commands

Arguments:

  * `device::Device`
  * `indirect_commands_layout::IndirectCommandsLayoutNV` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyIndirectCommandsLayoutNV.html)

```julia
_destroy_indirect_commands_layout_nv(
    device,
    indirect_commands_layout;
    allocator
)

```

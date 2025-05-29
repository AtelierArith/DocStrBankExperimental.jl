引数:

  * `device::Device`
  * `info::DeviceImageMemoryRequirements`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceImageSparseMemoryRequirements.html)

```julia
get_device_image_sparse_memory_requirements(
    device,
    info::Vulkan.DeviceImageMemoryRequirements
) -> Vector{Vulkan.SparseImageMemoryRequirements2}

```

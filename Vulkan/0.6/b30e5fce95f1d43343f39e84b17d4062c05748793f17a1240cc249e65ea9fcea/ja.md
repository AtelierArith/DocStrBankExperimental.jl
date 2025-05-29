引数:

  * `device::Device`
  * `image::Image` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyImage.html)

```julia
destroy_image(device, image; allocator)

```

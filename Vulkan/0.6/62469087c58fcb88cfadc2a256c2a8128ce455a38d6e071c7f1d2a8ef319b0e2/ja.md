引数:

  * `device::Device`
  * `image::Image` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyImage.html)

```julia
_destroy_image(device, image; allocator)

```

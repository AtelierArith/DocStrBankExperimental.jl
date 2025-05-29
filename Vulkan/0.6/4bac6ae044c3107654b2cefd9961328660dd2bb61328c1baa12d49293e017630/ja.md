引数:

  * `device::Device`
  * `image_view::ImageView` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyImageView.html)

```julia
destroy_image_view(device, image_view; allocator)

```

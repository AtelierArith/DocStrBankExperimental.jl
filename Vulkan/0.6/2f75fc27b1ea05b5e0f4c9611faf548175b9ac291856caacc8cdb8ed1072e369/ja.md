拡張: VK*EXT*image*compression*control

引数:

  * `device::Device`
  * `image::Image`
  * `subresource::_ImageSubresource2EXT`
  * `next_types::Type...`: `next` チェーンの一部として初期化し、含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageSubresourceLayout2EXT.html)

```julia
_get_image_subresource_layout_2_ext(
    device,
    image,
    subresource::Vulkan._ImageSubresource2EXT,
    next_types::Type...
) -> Vulkan._SubresourceLayout2EXT

```

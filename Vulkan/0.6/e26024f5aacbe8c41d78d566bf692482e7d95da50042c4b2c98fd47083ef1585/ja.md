拡張機能: VK*KHR*video*decode*queue

引数:

  * `flags::VideoDecodeCapabilityFlagKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeCapabilitiesKHR.html)

```julia
_VideoDecodeCapabilitiesKHR(
    flags::Vulkan.VideoDecodeCapabilityFlagKHR;
    next
) -> Vulkan._VideoDecodeCapabilitiesKHR

```

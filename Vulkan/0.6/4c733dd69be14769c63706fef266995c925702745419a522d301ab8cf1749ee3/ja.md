拡張: VK*KHR*incremental_present

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `regions::Vector{_PresentRegionKHR}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPresentRegionsKHR.html)

```julia
_PresentRegionsKHR(
;
    next,
    regions
) -> Vulkan._PresentRegionsKHR

```

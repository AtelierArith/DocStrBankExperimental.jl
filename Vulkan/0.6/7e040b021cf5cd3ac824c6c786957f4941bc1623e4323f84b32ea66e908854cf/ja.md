引数:

  * `reduction_mode::SamplerReductionMode`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerReductionModeCreateInfo.html)

```julia
_SamplerReductionModeCreateInfo(
    reduction_mode::Vulkan.SamplerReductionMode;
    next
) -> Vulkan._SamplerReductionModeCreateInfo

```

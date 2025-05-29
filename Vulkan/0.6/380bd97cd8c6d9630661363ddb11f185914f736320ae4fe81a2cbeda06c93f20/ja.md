引数:

  * `device::Device`
  * `ycbcr_conversion::SamplerYcbcrConversion` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySamplerYcbcrConversion.html)

```julia
destroy_sampler_ycbcr_conversion(
    device,
    ycbcr_conversion;
    allocator
)

```

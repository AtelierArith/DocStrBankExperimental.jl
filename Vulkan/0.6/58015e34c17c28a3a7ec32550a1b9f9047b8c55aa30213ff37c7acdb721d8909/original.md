Extension: VK_EXT_hdr_metadata

Arguments:

  * `device::Device`
  * `swapchains::Vector{SwapchainKHR}`
  * `metadata::Vector{HdrMetadataEXT}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSetHdrMetadataEXT.html)

```julia
set_hdr_metadata_ext(
    device,
    swapchains::AbstractArray,
    metadata::AbstractArray
)

```

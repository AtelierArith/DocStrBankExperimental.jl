Extension: VK_EXT_opacity_micromap

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `micromaps::Vector{MicromapEXT}`
  * `query_type::QueryType`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (must be a valid pointer with `data_size` bytes)
  * `stride::UInt`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkWriteMicromapsPropertiesEXT.html)

```julia
_write_micromaps_properties_ext(
    device,
    micromaps::AbstractArray,
    query_type::Vulkan.QueryType,
    data_size::Integer,
    data::Ptr{Nothing},
    stride::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```

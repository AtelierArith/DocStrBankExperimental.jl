拡張: VK*EXT*opacity_micromap

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `micromaps::Vector{MicromapEXT}`
  * `query_type::QueryType`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (必ず `data_size` バイトの有効なポインタである必要があります)
  * `stride::UInt`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkWriteMicromapsPropertiesEXT.html)

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

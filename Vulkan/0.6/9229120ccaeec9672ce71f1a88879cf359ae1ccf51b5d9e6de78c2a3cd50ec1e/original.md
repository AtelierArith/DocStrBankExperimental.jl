Arguments:

  * `header_size::UInt32`
  * `header_version::PipelineCacheHeaderVersion`
  * `vendor_id::UInt32`
  * `device_id::UInt32`
  * `pipeline_cache_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCacheHeaderVersionOne.html)

```julia
_PipelineCacheHeaderVersionOne(
    header_size::Integer,
    header_version::Vulkan.PipelineCacheHeaderVersion,
    vendor_id::Integer,
    device_id::Integer,
    pipeline_cache_uuid::NTuple{16, UInt8}
) -> Vulkan._PipelineCacheHeaderVersionOne

```

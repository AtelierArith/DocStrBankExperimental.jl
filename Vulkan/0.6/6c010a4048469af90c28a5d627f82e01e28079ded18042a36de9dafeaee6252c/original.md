High-level wrapper for VkPipelineCacheHeaderVersionOne.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCacheHeaderVersionOne.html)

```julia
struct PipelineCacheHeaderVersionOne <: Vulkan.HighLevelStruct
```

  * `header_size::UInt32`
  * `header_version::Vulkan.PipelineCacheHeaderVersion`
  * `vendor_id::UInt32`
  * `device_id::UInt32`
  * `pipeline_cache_uuid::NTuple{16, UInt8}`

High-level wrapper for VkApplicationInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkApplicationInfo.html)

```julia
struct ApplicationInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `application_name::String`
  * `application_version::VersionNumber`
  * `engine_name::String`
  * `engine_version::VersionNumber`
  * `api_version::VersionNumber`

Arguments:

  * `application_version::VersionNumber`
  * `engine_version::VersionNumber`
  * `api_version::VersionNumber`
  * `next::Any`: defaults to `C_NULL`
  * `application_name::String`: defaults to ``
  * `engine_name::String`: defaults to ``

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkApplicationInfo.html)

```julia
ApplicationInfo(
    application_version::VersionNumber,
    engine_version::VersionNumber,
    api_version::VersionNumber;
    next,
    application_name,
    engine_name
) -> Vulkan.ApplicationInfo

```

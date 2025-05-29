Arguments:

  * `application_version::VersionNumber`
  * `engine_version::VersionNumber`
  * `api_version::VersionNumber`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `application_name::String`: defaults to `C_NULL`
  * `engine_name::String`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkApplicationInfo.html)

```julia
_ApplicationInfo(
    application_version::VersionNumber,
    engine_version::VersionNumber,
    api_version::VersionNumber;
    next,
    application_name,
    engine_name
) -> Vulkan._ApplicationInfo

```

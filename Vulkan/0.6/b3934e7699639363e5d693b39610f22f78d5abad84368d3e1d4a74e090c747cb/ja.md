引数:

  * `application_version::VersionNumber`
  * `engine_version::VersionNumber`
  * `api_version::VersionNumber`
  * `next::Any`: デフォルトは `C_NULL`
  * `application_name::String`: デフォルトは ``
  * `engine_name::String`: デフォルトは ``

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkApplicationInfo.html)

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

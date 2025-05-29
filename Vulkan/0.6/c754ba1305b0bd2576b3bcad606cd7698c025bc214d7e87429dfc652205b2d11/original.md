Arguments:

  * `driver_id::DriverId`
  * `driver_name::String`
  * `driver_info::String`
  * `conformance_version::_ConformanceVersion`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDriverProperties.html)

```julia
_PhysicalDeviceDriverProperties(
    driver_id::Vulkan.DriverId,
    driver_name::AbstractString,
    driver_info::AbstractString,
    conformance_version::Vulkan._ConformanceVersion;
    next
)

```

Arguments:

  * `driver_id::DriverId`
  * `driver_name::String`
  * `driver_info::String`
  * `conformance_version::ConformanceVersion`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDriverProperties.html)

```julia
PhysicalDeviceDriverProperties(
    driver_id::Vulkan.DriverId,
    driver_name::AbstractString,
    driver_info::AbstractString,
    conformance_version::Vulkan.ConformanceVersion;
    next
) -> Vulkan.PhysicalDeviceDriverProperties

```

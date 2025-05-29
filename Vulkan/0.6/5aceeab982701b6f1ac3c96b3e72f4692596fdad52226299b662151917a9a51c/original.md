Extension: VK_KHR_ray_tracing_pipeline

Arguments:

  * `max_pipeline_ray_payload_size::UInt32`
  * `max_pipeline_ray_hit_attribute_size::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineInterfaceCreateInfoKHR.html)

```julia
_RayTracingPipelineInterfaceCreateInfoKHR(
    max_pipeline_ray_payload_size::Integer,
    max_pipeline_ray_hit_attribute_size::Integer;
    next
) -> Vulkan._RayTracingPipelineInterfaceCreateInfoKHR

```

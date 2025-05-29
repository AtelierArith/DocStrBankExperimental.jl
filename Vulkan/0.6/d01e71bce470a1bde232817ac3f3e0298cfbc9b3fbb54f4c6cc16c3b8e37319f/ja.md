拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `max_pipeline_ray_payload_size::UInt32`
  * `max_pipeline_ray_hit_attribute_size::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineInterfaceCreateInfoKHR.html)

```julia
RayTracingPipelineInterfaceCreateInfoKHR(
    max_pipeline_ray_payload_size::Integer,
    max_pipeline_ray_hit_attribute_size::Integer;
    next
) -> Vulkan.RayTracingPipelineInterfaceCreateInfoKHR

```

拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `device::Device`
  * `pipeline::Pipeline`
  * `group::UInt32`
  * `group_shader::ShaderGroupShaderKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetRayTracingShaderGroupStackSizeKHR.html)

```julia
get_ray_tracing_shader_group_stack_size_khr(
    device,
    pipeline,
    group::Integer,
    group_shader::Vulkan.ShaderGroupShaderKHR
) -> UInt64

```

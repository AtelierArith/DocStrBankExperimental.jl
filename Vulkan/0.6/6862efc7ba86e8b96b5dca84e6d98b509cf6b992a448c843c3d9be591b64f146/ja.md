拡張: VK*NV*ray*tracing*motion_blur

引数:

  * `ray_tracing_motion_blur::Bool`
  * `ray_tracing_motion_blur_pipeline_trace_rays_indirect::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingMotionBlurFeaturesNV.html)

```julia
_PhysicalDeviceRayTracingMotionBlurFeaturesNV(
    ray_tracing_motion_blur::Bool,
    ray_tracing_motion_blur_pipeline_trace_rays_indirect::Bool;
    next
) -> Vulkan._PhysicalDeviceRayTracingMotionBlurFeaturesNV

```

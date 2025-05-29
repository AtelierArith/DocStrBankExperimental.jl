Extension: VK_NV_ray_tracing_motion_blur

Arguments:

  * `ray_tracing_motion_blur::Bool`
  * `ray_tracing_motion_blur_pipeline_trace_rays_indirect::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingMotionBlurFeaturesNV.html)

```julia
_PhysicalDeviceRayTracingMotionBlurFeaturesNV(
    ray_tracing_motion_blur::Bool,
    ray_tracing_motion_blur_pipeline_trace_rays_indirect::Bool;
    next
) -> Vulkan._PhysicalDeviceRayTracingMotionBlurFeaturesNV

```

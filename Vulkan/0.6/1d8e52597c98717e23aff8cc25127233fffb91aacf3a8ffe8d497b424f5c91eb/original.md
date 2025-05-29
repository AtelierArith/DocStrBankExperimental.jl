Extension: VK_AMD_shader_info

Return codes:

  * `SUCCESS`
  * `ERROR_FEATURE_NOT_PRESENT`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `pipeline::Pipeline`
  * `shader_stage::ShaderStageFlag`
  * `info_type::ShaderInfoTypeAMD`

!!! warning
    The pointer returned by this function holds memory owned by Julia. It is therefore **your** responsibility to free it after use (e.g. with `Libc.free`).


[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetShaderInfoAMD.html)

```julia
get_shader_info_amd(
    device,
    pipeline,
    shader_stage::Vulkan.ShaderStageFlag,
    info_type::Vulkan.ShaderInfoTypeAMD
) -> ResultTypes.Result{Tuple{UInt64, Ptr{Nothing}}, Vulkan.VulkanError}

```

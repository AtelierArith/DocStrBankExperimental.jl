引数:

  * `storage_buffer_16_bit_access::Bool`
  * `uniform_and_storage_buffer_16_bit_access::Bool`
  * `storage_push_constant_16::Bool`
  * `storage_input_output_16::Bool`
  * `multiview::Bool`
  * `multiview_geometry_shader::Bool`
  * `multiview_tessellation_shader::Bool`
  * `variable_pointers_storage_buffer::Bool`
  * `variable_pointers::Bool`
  * `protected_memory::Bool`
  * `sampler_ycbcr_conversion::Bool`
  * `shader_draw_parameters::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkan11Features.html)

```julia
PhysicalDeviceVulkan11Features(
    storage_buffer_16_bit_access::Bool,
    uniform_and_storage_buffer_16_bit_access::Bool,
    storage_push_constant_16::Bool,
    storage_input_output_16::Bool,
    multiview::Bool,
    multiview_geometry_shader::Bool,
    multiview_tessellation_shader::Bool,
    variable_pointers_storage_buffer::Bool,
    variable_pointers::Bool,
    protected_memory::Bool,
    sampler_ycbcr_conversion::Bool,
    shader_draw_parameters::Bool;
    next
) -> Vulkan.PhysicalDeviceVulkan11Features

```

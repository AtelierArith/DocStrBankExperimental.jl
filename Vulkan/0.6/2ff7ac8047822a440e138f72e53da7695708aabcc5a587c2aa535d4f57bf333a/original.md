Extension: VK_EXT_extended_dynamic_state3

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `samples::SampleCountFlag`
  * `sample_mask::Vector{UInt32}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetSampleMaskEXT.html)

```julia
cmd_set_sample_mask_ext(
    command_buffer,
    samples::Vulkan.SampleCountFlag,
    sample_mask::AbstractArray
)

```

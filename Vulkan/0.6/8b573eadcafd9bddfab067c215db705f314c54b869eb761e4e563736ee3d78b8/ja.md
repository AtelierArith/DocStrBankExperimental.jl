拡張: VK*EXT*extended*dynamic*state3

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `samples::SampleCountFlag`
  * `sample_mask::Vector{UInt32}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdSetSampleMaskEXT.html)

```julia
_cmd_set_sample_mask_ext(
    command_buffer,
    samples::Vulkan.SampleCountFlag,
    sample_mask::AbstractArray
)

```

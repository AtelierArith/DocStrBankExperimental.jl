拡張: VK*AMD*shader_info

戻りコード:

  * `SUCCESS`
  * `ERROR_FEATURE_NOT_PRESENT`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `pipeline::Pipeline`
  * `shader_stage::ShaderStageFlag`
  * `info_type::ShaderInfoTypeAMD`

!!! 警告     この関数が返すポインタは、Juliaが所有するメモリを保持しています。したがって、使用後にそれを解放するのは**あなた**の責任です（例: `Libc.free`を使用して）。

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetShaderInfoAMD.html)

```julia
get_shader_info_amd(
    device,
    pipeline,
    shader_stage::Vulkan.ShaderStageFlag,
    info_type::Vulkan.ShaderInfoTypeAMD
) -> ResultTypes.Result{Tuple{UInt64, Ptr{Nothing}}, Vulkan.VulkanError}

```

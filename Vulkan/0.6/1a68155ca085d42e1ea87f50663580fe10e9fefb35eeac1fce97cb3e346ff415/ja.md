拡張機能: VK*NV*ray_tracing

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `pipeline::Pipeline`
  * `shader::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCompileDeferredNV.html)

```julia
_compile_deferred_nv(
    device,
    pipeline,
    shader::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```

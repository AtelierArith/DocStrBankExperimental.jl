拡張: VK*KHR*pipeline*executable*properties

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `executable_info::PipelineExecutableInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPipelineExecutableInternalRepresentationsKHR.html)

```julia
get_pipeline_executable_internal_representations_khr(
    device,
    executable_info::Vulkan.PipelineExecutableInfoKHR
) -> ResultTypes.Result{Vector{Vulkan.PipelineExecutableInternalRepresentationKHR}, Vulkan.VulkanError}

```

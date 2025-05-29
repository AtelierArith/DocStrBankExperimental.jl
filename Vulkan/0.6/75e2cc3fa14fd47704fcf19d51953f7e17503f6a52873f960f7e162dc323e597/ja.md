戻り値のコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `command_pool::CommandPool` (externsync)
  * `flags::CommandPoolResetFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkResetCommandPool.html)

```julia
reset_command_pool(
    device,
    command_pool;
    flags
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```

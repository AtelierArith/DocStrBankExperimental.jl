拡張: VK*AMD*memory*overallocation*behavior

引数:

  * `overallocation_behavior::MemoryOverallocationBehaviorAMD`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceMemoryOverallocationCreateInfoAMD.html)

```julia
DeviceMemoryOverallocationCreateInfoAMD(
    overallocation_behavior::Vulkan.MemoryOverallocationBehaviorAMD;
    next
) -> Vulkan.DeviceMemoryOverallocationCreateInfoAMD

```

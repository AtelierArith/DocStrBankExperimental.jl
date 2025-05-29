VkPipelineDepthStencilStateCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineDepthStencilStateCreateInfo.html)

```julia
struct PipelineDepthStencilStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineDepthStencilStateCreateFlag`
  * `depth_test_enable::Bool`
  * `depth_write_enable::Bool`
  * `depth_compare_op::Vulkan.CompareOp`
  * `depth_bounds_test_enable::Bool`
  * `stencil_test_enable::Bool`
  * `front::Vulkan.StencilOpState`
  * `back::Vulkan.StencilOpState`
  * `min_depth_bounds::Float32`
  * `max_depth_bounds::Float32`

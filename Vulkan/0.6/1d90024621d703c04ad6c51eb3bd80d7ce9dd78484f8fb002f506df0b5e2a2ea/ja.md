内部Vulkanデータを参照する不透明ハンドル。ファイナライザの登録はコンストラクタによって処理されます。

```julia
abstract type Handle <: Vulkan.VulkanStruct{false}
```

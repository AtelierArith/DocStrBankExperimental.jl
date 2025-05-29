標準Vulkanの拡張が有効かどうかを返します。つまり、指定されたシンボル `x` がコアであるか、無効になっていない拡張からのものであるか、またはVulkan SCに独占的でない場合です。

```julia
isenabled(x, extensions::VulkanSpec.Extensions) -> Any

```

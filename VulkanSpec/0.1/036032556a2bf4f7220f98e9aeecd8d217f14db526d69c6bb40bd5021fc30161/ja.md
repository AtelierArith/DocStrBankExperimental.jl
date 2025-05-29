`destroyed_param`の値として渡された`handle`を破壊する`func`関数。

`batch`がtrueの場合、`func`は複数のハンドルのリストを期待し、一度にすべてを破壊します。

```julia
struct DestroyFunc <: VulkanSpec.Spec
```

  * `func::VulkanSpec.SpecFunc`
  * `handle::VulkanSpec.SpecHandle`
  * `destroyed_param::VulkanSpec.SpecFuncParam`
  * `batch::Bool`

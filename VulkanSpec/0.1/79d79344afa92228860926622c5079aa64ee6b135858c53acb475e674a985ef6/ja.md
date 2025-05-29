`func`は、パラメータ`create_info_param`の値として渡された作成情報構造体`create_info_struct`から`handle`を作成します。

`batch`がtrueの場合、`func`は複数の作成情報構造体のリストを期待し、一度に複数のハンドルを作成します。

```julia
struct CreateFunc <: VulkanSpec.Spec
```

  * `func::VulkanSpec.SpecFunc`
  * `handle::VulkanSpec.SpecHandle`
  * `create_info_struct::Union{Nothing, VulkanSpec.SpecStruct}`
  * `create_info_param::Union{Nothing, VulkanSpec.SpecFuncParam}`
  * `batch::Bool`

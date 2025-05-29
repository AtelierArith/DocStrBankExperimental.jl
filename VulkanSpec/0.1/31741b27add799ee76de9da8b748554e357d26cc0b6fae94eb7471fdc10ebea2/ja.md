`const <name> = <alias>`の形式のエイリアスの仕様。

```julia
struct SpecAlias{S<:VulkanSpec.Spec} <: VulkanSpec.Spec
```

  * `name::Symbol`: 新しいエイリアスの名前。
  * `alias::VulkanSpec.Spec`: エイリアスされた仕様要素。

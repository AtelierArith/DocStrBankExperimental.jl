構造体の仕様。

```julia
struct SpecStruct <: VulkanSpec.Spec
```

  * `name::Symbol`: 構造体の名前。
  * `type::VulkanSpec.StructType`: [`StructType`](@ref) 分類。
  * `is_returnedonly::Bool`: 構造体がユーザーによって構築されるのではなく、Vulkan関数によってのみ記入されることを意図しているかどうか。

    APIは、特にクエリのための `pNext` チェーンの一部として、ユーザーに初期化された構造体を提供するよう要求する場合があります。
  * `extends::Vector{Symbol}`: 拡張する構造体の名前。通常は元の構造体の `pNext` 引数を通じて行われます。
  * `members::StructArrays.StructVector{VulkanSpec.SpecStructMember}`: 構造体のメンバー。

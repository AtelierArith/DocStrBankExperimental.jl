関数の仕様。

```julia
struct SpecFunc <: VulkanSpec.Spec
```

  * `name::Symbol`: 関数の名前。
  * `type::VulkanSpec.FunctionType`: [`FunctionType`](@ref) 分類。
  * `return_type::Union{Nothing, Expr, Symbol}`: 戻り値の型（`Nothing`の場合はvoid）。
  * `render_pass_compatibility::Vector{VulkanSpec.RenderPassRequirement}`: 関数がレンダーパス内、外、または両方で実行できるかどうか。指定されていない場合は空で、内部と外部の両方で実行可能であることと同等。
  * `queue_compatibility::Vector{VulkanSpec.QueueType}`: 関数が実行できるキューのタイプ。指定されていない場合は空で、すべてのキューで実行可能であることと同等。
  * `params::StructArrays.StructVector{VulkanSpec.SpecFuncParam}`: 関数のパラメータ。
  * `success_codes::Vector{Symbol}`
  * `error_codes::Vector{Symbol}`

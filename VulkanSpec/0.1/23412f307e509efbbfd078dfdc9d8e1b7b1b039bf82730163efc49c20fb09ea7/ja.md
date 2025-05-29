構造体パラメータの仕様。

```julia
struct SpecStructMember <: VulkanSpec.Spec
```

  * `parent::Any`: 親構造体の名前。
  * `name::Symbol`: 識別子。
  * `type::Union{Expr, Symbol}`: その慣用的なJulia型の式。
  * `is_constant::Bool`: 定数である場合、Vulkan関数によって変更できない。
  * `is_externsync::Bool`: 親構造体を使用する任意の関数を呼び出す前に外部で同期する必要があるかどうか。
  * `requirement::VulkanSpec.PARAM_REQUIREMENT`: [`PARAM_REQUIREMENT`](@ref) 分類。
  * `len::Union{Nothing, Expr, Symbol}`: その長さを表すメンバー（同じ構造体の）の名前。ベクトル型でない場合は`Nothing`。
  * `arglen::Vector{Union{Expr, Symbol}}`: その長さを持つメンバー（同じ構造体の）の名前。
  * `autovalidity::Bool`: 自動的な有効性ドキュメントが有効になっているかどうか。falseの場合、これはメンバーが少なくとも1つのVulkan規約の例外である可能性があることを意味する。

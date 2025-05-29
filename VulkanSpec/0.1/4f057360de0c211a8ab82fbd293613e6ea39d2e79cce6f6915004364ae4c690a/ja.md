関数パラメータの仕様。

```julia
struct SpecFuncParam <: VulkanSpec.Spec
```

  * `parent::Any`: 親関数の名前。
  * `name::Symbol`: 識別子。
  * `type::Union{Expr, Symbol}`: その慣用的なJulia型の式。
  * `is_constant::Bool`: 定数である場合、Vulkan関数によって変更できない。
  * `is_externsync::Bool`: 関数を呼び出す前に外部で同期する必要があるかどうか。
  * `requirement::VulkanSpec.PARAM_REQUIREMENT`: [`PARAM_REQUIREMENT`](@ref) 分類。
  * `len::Union{Nothing, Expr, Symbol}`: その長さを表すパラメータ（同じ関数の）の名前。ベクトル型でない場合は`Nothing`。パラメータの式であることもできる。
  * `arglen::Vector{Symbol}`: その長さを持つパラメータ（同じ関数の）の名前。
  * `autovalidity::Bool`: 自動的な有効性ドキュメントが有効かどうか。falseの場合、これはパラメータが少なくとも1つのVulkan規約の例外である可能性があることを意味する。

ユニオン型の仕様。

```julia
struct SpecUnion <: VulkanSpec.Spec
```

  * `name::Symbol`: ユニオン型の名前。
  * `types::Vector{Union{Expr, Symbol}}`: ユニオンの可能な型。
  * `fields::Vector{Symbol}`: 構造体をユニオン型にキャストするフィールド。
  * `selectors::Vector{Symbol}`: 特定の文脈（例えば関数呼び出し）でユニオンの型を決定するためのセレクタ値（ある場合）。
  * `is_returnedonly::Bool`: 構造体がユーザーによって構築されるのではなく、Vulkan関数によってのみ入力されることを意図しているかどうか。

    APIは、特にクエリのための `pNext` チェーンの一部として、ユーザーに初期化された構造体を提供するよう要求する場合があることに注意してください。

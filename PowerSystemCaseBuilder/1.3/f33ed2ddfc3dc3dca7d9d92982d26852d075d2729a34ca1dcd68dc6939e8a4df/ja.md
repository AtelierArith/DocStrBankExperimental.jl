build*system(     category::Type{<:SystemCategory},     name::String,     print*stat::Bool = false;     kwargs..., )

受け入れられるキーワード:

  * `force_build::Bool`: `true` は全ビルドプロセスを実行し、`false` (デフォルト) は可能であればデシリアライズを使用します
  * `skip_serialization::Bool`: デフォルトは `false`
  * `system_catalog::SystemCatalog`
  * `assign_new_uuids::Bool`: デシリアライズが使用される場合、システムとすべてのコンポーネントに新しいUUIDを割り当てます。デフォルトは `true`。

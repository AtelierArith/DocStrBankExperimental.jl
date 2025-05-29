```julia
make_selector(
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent};
    groupby,
    name
) -> InfrastructureSystems.TypeComponentSelector

```

指定されたコンポーネントの型から[`ComponentSelector`](@ref)を作成します。オプションで、セレクタのグループ化動作および/または名前を提供できます。この方法で構築されたセレクタは、`groupby`引数によってグループ化された指定された型のすべてのコンポーネントを指します（基本の[`make_selector`](@ref)ドキュメントを参照）。

# 引数

  * `component_type::Type{<:InfrastructureSystemsComponent}`: 選択するコンポーネントの型
  * `groupby::Union{Symbol, Function} = :each`: グループ化動作（基本の[`make_selector`](@ref)ドキュメントを参照）
  * `name::Union{String, Nothing} = nothing`: セレクタの名前; 提供されない場合は、自動的に構築されます

# 例

```julia
sel1 = make_selector(RenewableDispatch)
sel2 = make_selector(RenewableDispatch; groupby = :all)
sel3 = make_selector(RenewableDispatch; name = "my_selector")
```

参照: [`make_selector`](@ref) 統一関数ドキュメント

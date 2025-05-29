```julia
make_selector(
    content::InfrastructureSystems.ComponentSelector...;
    name
) -> InfrastructureSystems.ListComponentSelector

```

複数の既存の `ComponentSelector` から [`ComponentSelector`](@ref) を作成します。オプションでセレクタの名前を提供できます。この方法で構築されたセレクタは、構築に使用された各セレクタのグループを含みます。

# 引数

  * `content::ComponentSelector...`: グループを形成するセレクタのリスト
  * `name::Union{String, Nothing} = nothing`: セレクタの名前; 提供されない場合は、自動的に構築されます

# 例

```julia
sel1 = make_selector(make_selector(ThermalStandard), make_selector(RenewableDispatch))
sel2 = make_selector(make_selector(ThermalStandard), make_selector(RenewableDispatch); name = "my_selector")
```

参照: [`make_selector`](@ref) 統一関数のドキュメント

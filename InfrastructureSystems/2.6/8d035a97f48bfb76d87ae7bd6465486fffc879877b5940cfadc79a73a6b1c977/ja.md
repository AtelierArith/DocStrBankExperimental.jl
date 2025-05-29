```julia
make_selector(
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent},
    component_name::AbstractString;
    name
) -> InfrastructureSystems.NameComponentSelector

```

与えられたタイプと名前を持つ単一のコンポーネントを指す [`ComponentSelector`](@ref) を作成します。オプションで、セレクタの名前を提供できます。この方法で構築されたセレクタは、ターゲットコンポーネントが存在する場合は1つのコンポーネントを含む1つのグループを正確に含み、存在しない場合はゼロを含みます。

# 引数

  * `component_type::Type{<:InfrastructureSystemsComponent}`: ターゲットコンポーネントのタイプ
  * `component_name::AbstractString`: ターゲットコンポーネントの名前
  * `name::Union{String, Nothing} = nothing`: セレクタの名前; 提供されない場合は、自動的に構築されます

# 例

```julia
sel1 = make_selector(ThermalStandard, "322_CT_6")
sel2 = make_selector(ThermalStandard, "322_CT_6"; name = "my_selector")
```

参照: [`make_selector`](@ref) 統一関数ドキュメント

```julia
make_selector(
    component::InfrastructureSystems.InfrastructureSystemsComponent;
    name
) -> InfrastructureSystems.NameComponentSelector

```

コンポーネントから [`ComponentSelector`](@ref) を作成し、指定されたものと同じ型と名前を持つ単一のコンポーネントを指します。オプションでセレクタの名前を提供できます。この方法で構築されたセレクタは、ターゲットコンポーネントが存在する場合は1つのコンポーネントを含む1つのグループを正確に含み、存在しない場合は0を含みます。

# 引数

  * `component::InfrastructureSystemsComponent`: このセレクタのターゲットを指定する型と名前を持つコンポーネント
  * `name::Union{String, Nothing} = nothing`: セレクタの名前; 提供されない場合は、自動的に構築されます

# 例

```julia
sel1 = make_selector(my_component)
sel2 = make_selector(my_component; name = "my_selector")
```

参照: [`make_selector`](@ref) 統一関数ドキュメント

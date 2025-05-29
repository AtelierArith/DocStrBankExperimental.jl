```julia
make_selector(
    filter_func::Function,
    component_type::Type{<:InfrastructureSystems.InfrastructureSystemsComponent};
    name,
    groupby
) -> InfrastructureSystems.FilterComponentSelector

```

フィルタ関数とコンポーネントの型から [`ComponentSelector`](@ref) を作成します。フィルタ関数は `component_type` のインスタンスを唯一の引数として受け取り、`Bool` を返す必要があります。オプションで、グルーピングの動作やセレクタの名前を提供できます。この方法で構築されたセレクタは、フィルタ関数を満たす指定された型のすべてのコンポーネントを指し、`groupby` 引数によってグループ化されます（基本の [`make_selector`](@ref) ドキュメントを参照）。

# 引数

  * `filter_func::Function`: コンポーネントに適用するフィルタ関数
  * `component_type::Type{<:InfrastructureSystemsComponent}`: 選択するコンポーネントの型
  * `groupby::Union{Symbol, Function} = :each`: グルーピングの動作（基本の [`make_selector`](@ref) ドキュメントを参照）
  * `name::Union{String, Nothing} = nothing`: セレクタの名前; 提供されない場合は、自動的に構築されます

# 例

```julia
sel1 = make_selector(RenewableDispatch, x -> get_prime_mover_type(x) == PrimeMovers.PVe)
sel2 = make_selector(RenewableDispatch, x -> get_prime_mover_type(x) == PrimeMovers.PVe; groupby = :all)
sel3 = make_selector(RenewableDispatch, x -> get_prime_mover_type(x) == PrimeMovers.PVe; name = "my_selector")
```

参照: [`make_selector`](@ref) 統一関数ドキュメント

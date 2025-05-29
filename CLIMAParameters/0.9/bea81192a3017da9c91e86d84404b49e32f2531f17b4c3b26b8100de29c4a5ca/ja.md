```
get_parameter_values(
    pd::AbstractTOMLDict,
    names::Union{String,Vector{String}},
    component::String
)

get_parameter_values(
    pd::AbstractTOMLDict,
    name_map::Union{Dict, Vector{Pair}, NTuple{N, Pair}, Vararg{Pair}},
    component::String
)
```

TOML辞書とパラメータ名のリストを与えると、パラメータとその値のNamedTupleを返します。コンポーネントが指定されている場合、そのコンポーネントで使用されているパラメータとしてログに記録されます。

パラメータ名のリストの代わりに、パラメータ名からコード内の変数名へのイテラブルなマッピングを受け取ることができます。次に、この関数は長い名前からすべてのパラメータを取得し、キーが変数名であるNamedTupleを返します。

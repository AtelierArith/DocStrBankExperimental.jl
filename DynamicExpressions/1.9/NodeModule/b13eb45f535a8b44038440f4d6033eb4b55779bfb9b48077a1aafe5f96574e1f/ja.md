```
tree_mapreduce(
    f::Function,
    [f_branch::Function,]
    op::Function,
    tree::AbstractNode,
    [result_type::Type=Undefined];
    f_on_shared::Function=(result, is_shared) -> result,
    break_sharing::Val=Val(false),
)
```

木に関数を適用し、演算子 `op` を使用して結果を集約します。`op` は `(parent, child...) ->` の形式で定義されるべきで、単項演算子と二項演算子の両方を集約できるようにします。`op` は木の葉ノードに対しては呼び出されません。これは通常の `mapreduce` とは異なり、親ノードと子ノードに対して異なる処理を許可します。これが必要ない場合は、通常の `mapreduce` を使用することができます。引数 `break_sharing` は [`GraphNode`](@ref) の接続を切るために使用できます。

葉（変数/定数）ノードとブランチ（演算子）ノードのために別々の関数を提供することもできます。

# 例

```jldoctest
julia> operators = OperatorEnum(; binary_operators=[+, *]);

julia> tree = Node(; feature=1) + Node(; feature=2) * 3.2;

julia> tree_mapreduce(t -> 1, +, tree)  # ノードをカウントします。（通常の mapreduce も機能します）
5

julia> tree_mapreduce(t -> 1, (p, c...) -> p + max(c...), tree)  # 深さを計算します。通常の mapreduce は失敗します！
5

julia> tree_mapreduce(vcat, tree) do t
    t.degree == 2 ? [t.op] : UInt8[]
end  # 使用されている二項演算子のリストを取得します。（通常の mapreduce も機能します）
2-element Vector{UInt8}:
 1
 2

julia> tree_mapreduce(vcat, tree) do t
    (t.degree == 0 && t.constant) ? [t.val] : Float64[]
end  # 定数のリストを取得します。（通常の mapreduce も機能します）
1-element Vector{Float64}:
 3.2
```

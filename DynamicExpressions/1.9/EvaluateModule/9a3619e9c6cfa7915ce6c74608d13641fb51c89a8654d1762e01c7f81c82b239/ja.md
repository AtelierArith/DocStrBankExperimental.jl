```
eval_tree_array(
    tree::AbstractExpressionNode{T},
    cX::AbstractMatrix{T},
    operators::OperatorEnum;
    eval_options::Union{EvalOptions,Nothing}=nothing,
) where {T}
```

与えられた入力データ行列に対して二項木（方程式）を評価します。オペレーターには使用されるすべてのオペレーターが含まれています。この関数は、メモリ使用量を減らすためにダブレットとトリプレットの操作を融合します。

# 引数

  * `tree::AbstractExpressionNode`: 評価する木のルートノード。
  * `cX::AbstractMatrix{T}`: 木を評価するための入力データで、形状は `[num_features, num_rows]` です。
  * `operators::OperatorEnum`: 木で使用されるオペレーター。
  * `eval_options::Union{EvalOptions,Nothing}`: 異なる評価モードに関する文書は [`EvalOptions`](@ref) を参照してください。

# 戻り値

  * `(output, complete)::Tuple{AbstractVector{T}, Bool}`: 結果は1D配列であり、評価が成功裏に完了したかどうか（真/偽）も含まれます。`false` の complete は無限大または NaN が遭遇したことを意味し、大きな損失が方程式に割り当てられるべきです。

# 注意事項

この関数は次の擬似コードで表すことができます：

```
def eval(current_node)
    if current_node is leaf
        return current_node.value
    elif current_node is degree 1
        return current_node.operator(eval(current_node.left_child))
    else
        return current_node.operator(eval(current_node.left_child), eval(current_node.right_child))
```

コードの大部分は最適化と事前の NaN/Inf チェックのためのもので、評価を大幅に高速化します。

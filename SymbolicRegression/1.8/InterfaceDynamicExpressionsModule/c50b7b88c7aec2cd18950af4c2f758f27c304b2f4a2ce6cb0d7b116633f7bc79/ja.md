```
eval_tree_array(tree::Union{AbstractExpression,AbstractExpressionNode}, X::AbstractArray, options::AbstractOptions; kws...)
```

与えられた入力データ行列に対して二項木（方程式）を評価します。演算子には使用されるすべての演算子が含まれています。この関数は、メモリ使用量を減らすために、ダブレットとトリプレットの操作を融合します。

この関数は次の擬似コードで表すことができます：

```
function eval(current_node)
    if current_node is leaf
        return current_node.value
    elif current_node is degree 1
        return current_node.operator(eval(current_node.left_child))
    else
        return current_node.operator(eval(current_node.left_child), eval(current_node.right_child))
```

コードの大部分は最適化と事前のNaN/Infチェックに関するもので、評価を大幅に高速化します。

# 引数

  * `tree::Union{AbstractExpression,AbstractExpressionNode}`: 評価する木のルートノード。
  * `X::AbstractArray`: 木を評価するための入力データ。
  * `options::AbstractOptions`: 木で使用される演算子を定義するために使用されるオプション。

# 戻り値

  * `(output, complete)::Tuple{AbstractVector, Bool}`: 結果は1D配列であり、評価が成功裏に完了したかどうか（true/false）も含まれます。`false`のcompleteは無限大またはnanが発生したことを意味し、大きな損失が方程式に割り当てられるべきです。

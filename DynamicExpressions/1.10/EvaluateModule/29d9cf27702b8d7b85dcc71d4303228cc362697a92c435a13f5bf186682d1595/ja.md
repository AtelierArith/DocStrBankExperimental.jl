```
eval_tree_array(tree::AbstractExpressionNode, cX::AbstractMatrix, operators::GenericOperatorEnum; throw_errors::Bool=true)
```

与えられた入力データに対して、一般的な二項木（方程式）を評価します。入力データが何であれ構いません。`operators` 列挙型には使用されるすべての演算子が含まれています。通常の `OperatorEnum` を使用した `eval_tree_array` とは異なり、配列 `cX` は最初の次元に沿ってのみスライスされます。つまり、`cX` がベクトルであれば、特徴ノードの出力はスカラーになります。`cX` が3Dテンソルであれば、特徴ノードの出力は2Dテンソルになります。また、`tree.feature` は `cX` の最初の軸に沿ってインデックスされることに注意してください。

ただし、一般的に入力および出力の型に関する要件はありません。ツリーを設定して、一部の演算子ノードがテンソルで動作し、他の演算子ノードがスカラーで動作するようにすることができます。`eval_tree_array` は、特定の演算子が与えられた入力型に対して定義されていない場合、単に `nothing` を返します。

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

# 引数

  * `tree::AbstractExpressionNode`: 評価する木のルートノード。
  * `cX::AbstractArray`: 木を評価するための入力データ。
  * `operators::GenericOperatorEnum`: 木で使用される演算子。
  * `throw_errors::Bool=true`: 評価中にエラーが発生した場合にエラーをスローするかどうか。そうでない場合、メソッドエラーは発生する前にキャッチされ、評価はエラーをスローするのではなく `nothing` を返します。これは、特定のツリーが有効かどうか不明な場合に便利で、出力として `nothing` を使用することを好む場合に役立ちます。

# 戻り値

  * `(output, complete)::Tuple{Any, Bool}`: 結果と、評価が成功裏に完了したかどうか（真/偽）。評価が失敗した場合、最初の引数には `nothing` が返されます。`false` の complete は、演算子が定義されていない入力型に対して呼び出されたことを意味します。

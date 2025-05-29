# 概要

`abstract type AbstractUpdate <: Function`

通常、`(tree::FelNode, models; partition_list=1:length(tree.message))`を受け取り、`tree`と`models`を更新し、更新された`tree`と`models`を返す呼び出し可能な型です。

# 例

新しいサブタイプを定義します。ここで`foo`と`bar`は任意の更新関数です。

```julia
struct MyUpdate <: AbstractUpdate end

function (update::MyUpdate)(tree::FelNode, models; partition_list=1:length(tree.message))
    tree, models = foo(tree, models, partition_list=partition_list)
    tree, models = BayesUpdate(nni=0)(tree, models, partition_list=partition_list)
    tree, models = bar(tree, models, partition_list=partition_list)
    return tree, models
end
```

参照: [`StandardUpdate`](@ref)

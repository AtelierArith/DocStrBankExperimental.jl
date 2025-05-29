# Summary

`abstract type AbstractUpdate <: Function`

A callable type that typically takes `(tree::FelNode, models; partition_list=1:length(tree.message))`, updates `tree` and `models`, and returns the updated `tree` and `models`.

# Example

Define a new subtype, where `foo` and `bar` are arbitrary updating functions

```julia
struct MyUpdate <: AbstractUpdate end

function (update::MyUpdate)(tree::FelNode, models; partition_list=1:length(tree.message))
    tree, models = foo(tree, models, partition_list=partition_list)
    tree, models = BayesUpdate(nni=0)(tree, models, partition_list=partition_list)
    tree, models = bar(tree, models, partition_list=partition_list)
    return tree, models
end
```

See also: [`StandardUpdate`](@ref)

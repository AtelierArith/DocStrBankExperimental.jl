```
set_optimizer(
    model::GenericModel,
    optimizer_factory;
    add_bridges::Bool = true,
    kwargs...,
)
```

空の [`MOI.AbstractOptimizer`](@ref) インスタンスを `optimizer_factory` に対して [`MOI.instantiate`](@ref) を呼び出すことで作成し、それを `model` のオプティマイザとして設定します。

具体的には、`optimizer_factory` は引数なしで呼び出せる必要があり、空の [`MOI.AbstractOptimizer`](@ref) を返さなければなりません。

`add_bridges` が true の場合、オプティマイザによってサポートされていない制約や目的は、自動的に同等のサポートされている定式化にブリッジされます。`add_bridges = false` を渡すことで、ソルバーが `model` のすべての要素をネイティブにサポートしている場合、パフォーマンスが向上する可能性があります。

追加の `kwargs` は [`MOI.instantiate`](@ref) に渡されます。

オプティマイザのソルバー固有のパラメータを設定するには、[`set_attribute`](@ref) を参照してください。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model();

julia> set_optimizer(model, () -> HiGHS.Optimizer())

julia> set_optimizer(model, HiGHS.Optimizer; add_bridges = false)
```

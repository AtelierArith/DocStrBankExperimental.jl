```
set_optimizer(
    model::Model,
    optimizer_factory;
    add_bridges::Bool = true,
)
```

`optimizer_factory()`を呼び出すことで空の`MathOptInterface.AbstractOptimizer`インスタンスを作成し、それを`model`のオプティマイザとして設定します。具体的には、`optimizer_factory`は引数なしで呼び出せる必要があり、空の`MathOptInterface.AbstractOptimizer`を返さなければなりません。

`add_bridges`がtrueの場合、オプティマイザによってサポートされていない制約や目的は、自動的に同等のサポートされている定式化にブリッジされます。`add_bridges = false`を渡すことで、ソルバーが`model`内のすべての要素をネイティブにサポートしている場合、パフォーマンスが向上する可能性があります。

オプティマイザのソルバー固有のパラメータを設定するには、[`set_optimizer_attributes`](@ref)および[`set_optimizer_attribute`](@ref)を参照してください。

## 例

```julia
model = Model()
set_optimizer(model, HiGHS.Optimizer)
set_optimizer(model, HiGHS.Optimizer; add_bridges = false)
```

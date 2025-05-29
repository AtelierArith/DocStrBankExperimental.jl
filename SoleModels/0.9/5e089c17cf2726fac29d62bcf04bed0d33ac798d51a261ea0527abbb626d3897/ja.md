```
wrap(o::Any, FM::Type{<:AbstractModel})
wrap(m::AbstractModel)
wrap(o::Any)::AbstractModel
```

この関数は、任意のものをAbstractModelにラップします。デフォルトの動作は次のとおりです：     - `AbstractModel`に対して呼び出された場合、モデルは単に返されます（ラップは行われません）；     - `Function`と`FunctionWrapper`は[`FunctionModel`](@ref)にラップされます；     - その他のすべてのオブジェクトは`ConstantModel`にラップされます。

さらに[`AbstractModel`](@ref)、[`ConstantModel`](@ref)、[`FunctionModel`](@ref)、[`LeafModel`](@ref)を参照してください。

```
model_convert(
    model::AbstractModel,
    rhs::Union{
        AbstractConstraint,
        Number,
        AbstractJuMPScalar,
        MOI.AbstractSet,
    },
)
```

`rhs`の関数と集合の係数および定数を、係数型`value_type(typeof(model))`に変換します。

## 目的

制約を作成して追加するのは二段階のプロセスです。最初のステップでは[`build_constraint`](@ref)が呼び出され、その結果が[`add_constraint`](@ref)に渡されます。

しかし、[`build_constraint`](@ref)は`model`を引数として取らないため、関数または集合の係数および定数は`value_type(typeof(model))`とは異なる可能性があります。

したがって、[`build_constraint`](@ref)の結果は、[`add_constraint`](@ref)に渡される前に`model_convert`の呼び出しで変換されます。

```
const ADSelector = Union{
    ADTypes.AbstractADType,
    WrappedADSelector
}
```

インスタンスは自動微分バックエンドを指定します。

[`ADTypes.AbstractADType`](https://github.com/SciML/ADTypes.jl) のサブタイプ、または [`AutoDiffOperators.FwdRevADSelector`](@ref) のようなADセレクタラッパーです。

AutoDiffOperatorsは現在、次のADセレクタの独自の実装を提供しています: `AutoForwardDiff()`, `AutoFiniteDifferences()`, `AutoZygote()` および `AutoEnzyme()`。

これらのバックエンドのための `ADSelector`（特に `ADTypes.AbstractADType`）インスタンスは、モジュールおよびモジュール名から直接構築できます（`AutoDiffOperators` のデフォルトバックエンドパラメータを使用）:

```julia
import ForwardDiff
ADSelector(ForwardDiff)
ADSelector(:ForwardDiff)
ADSelector(Val(:ForwardDiff))
convert(ADSelector, ForwardDiff)
convert(ADSelector, :ForwardDiff)
convert(ADSelector, Val(:ForwardDiff))
```

ただし、特に順方向モードまたは逆方向モードのADを必要とするいくつかの操作は、これらのバックエンドのサブセットのみを受け入れます。

あるいは、[`DifferentiationInterface`](https://github.com/gdalle/DifferentiationInterface.jl) を使用して、`DiffIfAD(backend::ADTypes.AbstractADType)` をADセレクタとして使用することで、さまざまなADバックエンドとインターフェースを取ることができます。

# 実装

次の関数は `ADSelector` のサブタイプに特化する必要があります: [`with_jvp`](@ref), [`with_vjp_func`](@ref)。

[`AutoDiffOperators.supports_structargs`](@ref) は、該当する場合に特化する必要があります。

[`with_gradient`](@ref) のためにデフォルトの実装が提供されていますが、特化した実装の方がしばしばパフォーマンスが向上する可能性があります。

順方向および/または逆方向モードのADを他のセレクタタイプまたはADバックエンドに委譲するセレクタタイプは、[`forward_ad_selector`](@ref) および [`reverse_ad_selector`](@ref) を特化する必要があります。

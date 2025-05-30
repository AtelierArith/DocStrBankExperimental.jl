```
BridgeableConstraint(
    constraint::C,
    bridge_type::B;
    coefficient_type::Type{T} = Float64,
) where {C<:AbstractConstraint,B<:Type{<:MOI.Bridges.AbstractBridge},T}
```

[`AbstractConstraint`](@ref) は、`bridge_type{coefficient_type}` のブリッジによってブリッジ可能な `constraint` を表します。

モデルに `BridgeableConstraint` を追加することは、次の操作と同等です：

```julia
add_bridge(model, bridge_type; coefficient_type = coefficient_type)
add_constraint(model, constraint)
```

## 例

新しいスカラーセット型 `CustomSet` と、`F`-in-`CustomSet` 制約をブリッジできるブリッジ `CustomBridge` があるとします。ユーザーが次のように行った場合：

```julia
model = Model()
@variable(model, x)
@constraint(model, x + 1 in CustomSet())
optimize!(model)
```

`F`-in-`CustomSet` 制約をサポートしないオプティマイザを使用している場合、最初に `add_bridge(model, CustomBridge)` を呼び出さない限り、制約はブリッジされません。

`F`-in-`CustomSet` が追加される任意のモデルに `CustomBridge` を自動的に追加するには、次のメソッドを追加します：

```julia
function JuMP.build_constraint(
    error_fn::Function,
    func::AbstractJuMPScalar,
    set::CustomSet,
)
    constraint = ScalarConstraint(func, set)
    return BridgeableConstraint(constraint, CustomBridge)
end
```

## 注意

JuMP 拡張は、`CustomSet` を定義している場合にのみ `JuMP.build_constraint` を拡張すべきです。その理由は三つあります：

1. 複数の拡張が同じ JuMP メソッドをオーバーロードすると問題が発生します。
2. メソッドが欠けていると、ユーザーは `build_constraint` メソッドを定義している拡張モジュールを読み込むのを忘れたことに気づきません。
3. 関数や引数の型がパッケージ内で定義されていないメソッドを定義することは、[*型の略奪*](https://docs.julialang.org/en/v1/manual/style-guide/index.html#Avoid-type-piracy-1) と呼ばれ、Julia スタイルガイドでは推奨されていません。

```

```
struct BridgeableConstraint{C, B} <: AbstractConstraint
    constraint::C
    bridge_type::B
end
```

制約 `constraint` は、`bridge_type` のブリッジによってブリッジ可能です。この制約をモデルに追加することは、次のことと同等です。

```julia
add_bridge(model, bridge_type)
add_constraint(model, constraint)
```

## 例

新しいスカラーセット型 `CustomSet` と、`CustomSet` 制約をブリッジできるブリッジ `CustomBridge` があるとします。ユーザーが次のように行った場合：

```julia
model = Model()
@variable(model, x)
@constraint(model, x + 1 in CustomSet())
optimize!(model)
```

`F`-in-`CustomSet` 制約をサポートしないオプティマイザを使用している場合、ユーザーが手動で `add_bridge(model, CustomBridge)` を呼び出さない限り、制約はブリッジされません。`F`-in-`CustomSet` が追加される任意のモデルに `CustomBridge` を自動的に追加するには、次のメソッドを追加するだけです：

```julia
function JuMP.build_constraint(_error::Function, func::AbstractJuMPScalar,
                               set::CustomSet)
    constraint = ScalarConstraint(func, set)
    return JuMP.BridgeableConstraint(constraint, CustomBridge)
end
```

### 注意

JuMP 拡張は、`CustomSet` を定義した場合にのみ `JuMP.build_constraint` を拡張すべきです。理由は三つあります：

1. 複数の拡張が同じ JuMP メソッドをオーバーロードすると問題が発生します。
2. メソッドが欠けていると、ユーザーは `build_constraint` メソッドを定義する拡張モジュールを読み込むのを忘れたことに気づきません。
3. 関数や引数の型がパッケージ内で定義されていないメソッドを定義することは、[*型の略奪*](https://docs.julialang.org/en/v1/manual/style-guide/index.html#Avoid-type-piracy-1) と呼ばれ、Julia スタイルガイドでは推奨されていません。

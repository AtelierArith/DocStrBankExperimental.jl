```
jacobian!(∇c, con::AbstractConstraint, z, i=1)       # ステージ制約
jacobian!(∇c, con::AbstractConstraint, z1, z2, i=1)  # 結合制約
```

ノットポイント `z` で制約 `con` を評価します。デフォルトでは、このメソッドは次のように呼び出そうとします。

```
jacobian!(∇c, con, x)
```

`con` が `StateConstraint` の場合、

```
jacobian!(∇c, con, u)
```

`con` が `ControlConstraint` の場合、または

```
jacobian!(∇c, con, x, u)
```

`con` が `StageConstraint` の場合です。`con` が `CoupledConstraint` の場合、制約は次のように定義する必要があります。

```
jacobian!(∇c, con, z, i)
```

ここで `i` はどのヤコビアンを評価するかを決定します。例えば、`i = 1` の場合、最初のノットポイントのステージと制御に関するヤコビアンが計算されます。

# 自動微分

`con` が `StateConstraint` または `ControlConstraint` の場合、このメソッドは自動的に ForwardDiff を使用して定義されます。

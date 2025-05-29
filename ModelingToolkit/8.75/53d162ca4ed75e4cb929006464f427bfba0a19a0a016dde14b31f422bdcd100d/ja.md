```julia
equation_dependencies(sys::AbstractSystem; variables = states(sys))
```

`AbstractSystem` に対して、各方程式が依存する変数を計算します。

注意:

  * `variables` に含まれない変数はフィルタリングされます。
  * 与えられた方程式内の変数を決定するために `get_variables!` が使用されます。
  * 方程式のインデックスを依存する `variables` にマッピングする `Vector{Vector{Variable}}()` を返します。

例:

```julia
using ModelingToolkit
@parameters β γ κ η
@variables t S(t) I(t) R(t)

rate₁ = β * S * I
rate₂ = γ * I + t
affect₁ = [S ~ S - 1, I ~ I + 1]
affect₂ = [I ~ I - 1, R ~ R + 1]
j₁ = ModelingToolkit.ConstantRateJump(rate₁, affect₁)
j₂ = ModelingToolkit.VariableRateJump(rate₂, affect₂)

# これらのジャンプを使用して JumpSystem を作成
@named jumpsys = JumpSystem([j₁, j₂], t, [S, I, R], [β, γ])

# 各ジャンプレート関数の状態変数に対する依存関係
equation_dependencies(jumpsys)

# 各ジャンプレート関数のパラメータに対する依存関係
equation_dependencies(jumpsys, variables = parameters(jumpsys))
```

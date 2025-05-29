```
ShiftStrategy
```

ノルムを制御するための戦略を定義するための抽象型であり、潜在的に `shift` を更新することによって制御します。 [`ProjectorMonteCarloProblem`](@ref) または [`FCIQMC`](@ref) にパラメータとして渡されます。

## 実装された戦略:

  * [`DontUpdate`](@ref)
  * [`DoubleLogUpdate`](@ref) - [`ProjectorMonteCarloProblem()`](@ref) のデフォルト
  * [`LogUpdate`](@ref)
  * [`LogUpdateAfterTargetWalkers`](@ref) - FCIQMC標準
  * [`DoubleLogUpdateAfterTargetWalkers`](@ref)

# 拡張ヘルプ

内部的にカスタム戦略を実装するには、`Rimu.ShiftStrategy` の新しいサブタイプを定義し、以下のメソッドを実装します:

  * [`Rimu.update_shift_parameters!`](@ref) - `shift_parameters` を更新するため
  * [`Rimu.initialise_shift_parameters`](@ref) - (オプション) `shift_parameters` のカスタム実装を初期化および構築するため。デフォルトの実装は [`Rimu.DefaultShiftParameters`](@ref) です。

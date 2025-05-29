```
プロセス
```

新しいプロセスは `Process` をサブタイプ化し、[`processes_to_mtkmodel`](@ref) で使用できます。このタイプは、モジュール `ProcessBasedModelling` から以下の関数を拡張する必要があります：

  * `lhs_variable(p)` はプロセスが記述する変数（左辺変数）を返します。フィールドが存在する場合、デフォルトの実装は `lhs_variable(p) = p.variable` です。
  * `rhs(p)` は右辺の式、すなわち「実際の」プロセスです。
  * （オプション）`timescale(p)` はデフォルトで [`NoTimeDerivative`](@ref) です。
  * （オプション）`lhs(p)` は左辺を返します。`τ = timescale(p)` とします。デフォルトの `lhs(p)` の動作は `τ` に依存します：

      * `τ == NoTimeDerivative()` の場合は単に `lhs_variable(p)` です。
      * `τ == nothing` の場合は `Differential(t)(p)` であり、または `τ` が `LiteralParameter` の場合は数値で乗算されます。
      * `τ isa Union{Real, Num}` の場合は `τ_var*Differential(t)(p)` です。実数の場合、新しい名前付きパラメータ `τ_var` が作成され、プレフィックス `:τ_` と lhs-変数名が付けられ、デフォルト値は `τ` です。`Num` の場合は、`τ_var = τ` とします。
      * 上記が適さない場合は、`lhs_variable` を明示的に拡張してください。

```julia
JumpInputs(rs::ReactionSystem, u0, tspan,
            p = DiffEqBase.NullParameters;
            name = nameof(rs),
            combinatoric_ratelaws = get_combinatoric_ratelaws(rs),
            checks = false, physical_scales = nothing, 
            expand_catalyst_funs = true, 
            save_positions = (true, true),
            remake_warn = true, kwargs...)
```

与えられた反応系のためにJumpProblemを構築するための入力を生成します。

キーワード引数とデフォルト値:

  * `combinatoric_ratelaws=true` は、レート法則を計算する際に階乗スケーリング因子を使用します。すなわち、`2S -> 0` のレート `k` に対して、レート法則は `k*S*(S-1)/2!` になります。`combinatoric_ratelaws=false` に設定すると、レート法則は `k*S*(S-1)` になり、スケーリング因子は無視されます。デフォルトは、`ReactionSystem` が構築されたときに与えられた値（デフォルトはtrue）です。
  * `expand_catalyst_funs = true` は、別のシステムタイプに変換する際に、`hill(A,B,C,D)` のようなCatalystで定義された関数をその有理関数表現に置き換えます。無効にするには `false` に設定します。
  * `remake_warn = true` は、`true` の場合、システムにODE、可変レートジャンプ、または連続イベントが含まれている場合に警告が表示されます。これは、`remake` がそのような問題に対して機能しないためであり、パラメータや初期条件の値を変更したい場合は、`JumpInputs` と `JumpProblem` の両方を再度呼び出す必要があります。この警告は、`remake_warn = false` を渡すことで無効にできます。
  * `save_positions = (true, true)` は、`VariableRateJump` として分類された任意の反応について、ジャンプが発生する前後に解を保存するかどうかを示します。両方ともデフォルトはtrueです。

例:

```julia
using Catalyst, OrdinaryDiffEqTsit5, JumpProcesses, Plots
rn = @reaction_network begin
    k*(1 + sin(t)), 0 --> A
end
jinput = JumpInputs(rn, [:A => 0], (0.0, 10.0), [:k => .5])
@assert jinput.prob isa ODEProblem
jprob = JumpProblem(jinput)
sol = solve(jprob, Tsit5())
plot(sol, idxs = :A)

rn = @reaction_network begin
    k, 0 --> A
end
jinput = JumpInputs(rn, [:A => 0], (0.0, 10.0), [:k => .5])
@assert jinput.prob isa DiscreteProblem
jprob = JumpProblem(jinput)
sol = solve(jprob)
plot(sol, idxs = :A)
```

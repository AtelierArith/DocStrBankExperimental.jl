```julia
struct VariableRateJump{R, F, R2, R3, R4, I, T, T2} <: JumpProcesses.AbstractJump
```

時間に明示的に依存するレート（すなわち、ハザード、強度、または傾向）を持つジャンププロセスを定義します。より正確には、ジャンプの発生の*間*にレート関数が変化することが許可されているものです。詳細な例と使用情報については、以下を参照してください。

  * [Tutorial](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)

現在、異なるパフォーマンス特性を持つ2種類の`VariableRateJump`がサポートされています。

  * 一般的な`VariableRateJump`または`VariableRateJump`は、`rate`および`affect`関数のみが指定されているものを指します。

      * これらは表現できる内容において最も一般的ですが、時間の進行を処理する基盤のタイムステッパーを持つ`ODEProblem`または`SDEProblem`の使用が必要です（コールバックインターフェースを介して）。
      * これはシミュレーションにおいて最もパフォーマンスが低いジャンプタイプです。
  * 制約付き`VariableRateJump`は、関数`urate(u, p, t)`および`rateinterval(u, p, t)`に対応するキーワード引数`urate`および`rateinterval`を渡す必要があります。これらはレート関数が定数によって制約される時間ウィンドウを計算する必要があります。`u`の変化が他の`ConstantRateJump`、`MassActionJump`、または*制約付き*`VariableRateJump`の実行から生じる場合、時間間隔内でレートの制約が違反されることは問題ありません。選択された集約器がレートの制約と間隔を再計算するためです。*ただし、連続ダイナミクス（例えば、結合ODE、SDE、または一般的な`VariableRateJump`）から生じる`u`の変化によって時間間隔内で制約が違反される可能性がある場合、制約を与えるべきではありません。*これにより、ジャンプは一般的な`VariableRateJump`として分類され、適切に処理されます。また、オプションで下限関数`lrate(u, p, t)`を`lrate`キーワード引数を介して提供することもできます。これによりパフォーマンスが向上する可能性があります。下限の有効性は、`urate`と同じ条件およびレート間隔の下で保持されるべきです。

      * 制約付き`VariableRateJump`は現在`Coevolve`集約器で使用できるため、`SSAStepper`タイムステッパーを使用して純ジャンプ`DiscreteProblem`で効率的にシミュレーションできます。
      * これらはレート制約関数なしの一般的な`VariableRateJump`よりも大幅にパフォーマンスが向上する可能性があります。

再度強調しますが、制約付き`VariableRateJump`によって活用される追加のユーザー提供関数、`urate(u, p, t)`、`rateinterval(u, p, t)`、およびオプションの`lrate(u, p, t)`は以下を要求します。

  * `s`が`[t, t + rateinterval(u, p, t)]`の範囲にある場合、`lrate(u, p, t) <= rate(u, p, s) <= urate(u, p, t)`が成り立ちます。
  * これらの制約が他の`ConstantRateJump`、`MassActionJump`、または制約付き`VariableRateJump`が発生することによって時間ウィンドウ内で違反されることは問題ありません。ただし、`u`が他の理由（例えば、ODE、SDE、または一般的な`VariableRateJump`のような連続ダイナミクス）によって変化した場合には、有効でなければなりません。

## フィールド

  * `rate`: 状態`u`、パラメータ`p`、および時間`t`が与えられたときにジャンプの現在のレートを返す関数`rate(u,p,t)`。
  * `affect!`: `integrator`が与えられたときにジャンプの1回の発生のために状態を更新する関数`affect!(integrator)`。
  * `lrate`: 状態`u`およびパラメータ`p`が与えられたときに、時間`t`から`t + rateinterval(u, p, t)`の間のレートの下限を計算するオプションの関数`lrate(u, p, t)`。この制約は、他の`ConstantRateJump`、`MassActionJump`、または*制約付き*`VariableRateJump`がサンプリングされていない限り、時間間隔中に厳密に保持されなければなりません。制約付き`VariableRateJump`をサポートする集約器（現在は`Coevolve`のみ）を使用する場合、下限を提供することでパフォーマンスが向上する可能性があります。
  * `urate`: 一般的な`VariableRateJump`用のオプションの関数ですが、制約付き`VariableRateJump`を定義するためには必要であり、サポートする集約器（現在は`Coevolve`のみ）で使用でき、計算パフォーマンスが向上します。状態`u`およびパラメータ`p`が与えられたときに、時間`t`から`t + rateinterval(u, p, t)`の間のレートの上限を計算します。この制約は、他の`ConstantRateJump`、`MassActionJump`、または*制約付き*`VariableRateJump`がサンプリングされていない限り、時間間隔中に厳密に保持されなければなりません。
  * `rateinterval`: 一般的な`VariableRateJump`用のオプションの関数ですが、制約付き`VariableRateJump`を定義するためには必要であり、サポートする集約器（現在は`Coevolve`のみ）で使用でき、計算パフォーマンスが向上します。状態`u`およびパラメータ`p`が与えられたときに、`urate`および`lrate`の制約が保持される時間間隔を計算します。時間`t`から`t + rateinterval(u, p, t)`の間の制約は、他の`ConstantRateJump`、`MassActionJump`、または*制約付き*`VariableRateJump`がサンプリングされていない限り、時間間隔中に厳密に保持されなければなりません。
  * `idxs`
  * `rootfind`
  * `interp_points`
  * `save_positions`
  * `abstol`
  * `reltol`

## 例

`u[1]`が粒子の数を示し、`t*p[1]`が各粒子が消失する確率を時間ごとに示すとします。このジャンププロセスに対応する`VariableRateJump`は次のようになります。

```julia
rate(u,p,t) = t*p[1]*u[1]
affect!(integrator) = integrator.u[1] -= 1
vrj = VariableRateJump(rate, affect!)
```

サポートする集約器（例えば`Coevolve`）で使用できる制約付き`VariableRateJump`を定義するには、制約とレート間隔を定義する必要があります。

```julia
rateinterval(u,p,t) = (1 / p[1]) * 2
rate(u,p,t) = t * p[1] * u[1]
lrate(u, p, t) = rate(u, p, t)
urate(u,p,t) = rate(u, p, t + rateinterval(u,p,t))
affect!(integrator) = integrator.u[1] -= 1
vrj = VariableRateJump(rate, affect!; lrate = lrate, urate = urate,
                                      rateinterval = rateinterval)
```

## 注意事項

  * 制約付き`VariableRateJump`をサポートする集約器を使用する場合、`DiscreteProblem`を使用できます。そうでない場合は、`ODEProblem`または`SDEProblem`を使用する必要があります。
  * **制約付き`VariableRateJump`をサポートする集約器を使用しない場合、または一般的な`VariableRateJump`がある場合、`integrator`は主な状態ベクトルをラップする効果的な状態タイプを保持します。** このオブジェクトの使用に関する詳細は[`ExtendedJumpArray`](@ref)を参照してください。この場合、すべての`ConstantRateJump`、`VariableRateJump`およびコールバック`affect!`関数は、`integrator.u`が[`ExtendedJumpArray`](@ref)である`integrator`を受け取ります。
  * Salis H., Kaznessis Y.,  Accurate hybrid stochastic simulation of a system of coupled chemical or biochemical reactions, Journal of Chemical Physics, 122 (5), DOI:10.1063/1.1835951は、ODE/SDEインテグレーター内で`VariableRateJump`を使用してジャンプ時間を計算するために使用されます。

```

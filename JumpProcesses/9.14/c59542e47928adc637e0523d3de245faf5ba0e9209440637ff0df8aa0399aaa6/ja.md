```julia
struct ConstantRateJump{F1, F2} <: JumpProcesses.AbstractJump
```

時間に*明示的に*依存しないレート（すなわちハザード、強度、または傾向）を持つジャンププロセスを定義します。より正確には、ジャンプの発生の間にレート関数が一定であるものです。詳細な例と使用情報については、以下を参照してください。

  * [チュートリアル](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)

## フィールド

  * `rate`: ジャンプの現在のレートを返す関数 `rate(u,p,t)`。
  * `affect!`: ジャンプの1回の発生のために状態を更新する関数 `affect(integrator)`。

## 例

`u[1]` が粒子の数を示し、`p[1]` が各粒子が時間あたりに崩壊する確率を示すとします。このジャンププロセスに対応する `ConstantRateJump` は次のようになります。

```julia
rate(u,p,t) = p[1]*u[1]
affect!(integrator) = integrator.u[1] -= 1
crj = ConstantRateJump(rate, affect!)
```

ここで注意すべきは、`rate` は時間に応じて変化しますが、ジャンプの発生の間は一定であることです（`u[1]` が減少する時）。

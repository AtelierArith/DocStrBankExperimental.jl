```julia
struct MassActionJump{T, S, U, V} <: JumpProcesses.AbstractMassActionJump
```

質量作用形式で表現できる `ConstantRateJump` の最適化された表現であり、`ConstantRateJump` と比較してジャンプアルゴリズム内でのパフォーマンスが向上します。詳細な例や使用情報については、以下を参照してください。

  * [Main Docs](https://docs.sciml.ai/JumpProcesses/stable/jump_types/#Defining-a-Mass-Action-Jump)
  * [Tutorial](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)

### コンストラクタ

  * `MassActionJump(reactant_stoich, net_stoich; scale_rates = true, param_idxs = nothing)`

ここで `reactant_stoich` は各反応の反応物のストイキオメトリを示し、`net_stoich` は各反応のネットストイキオメトリを示します。

## フィールド

  * `scaled_rates`: (スケーリングされた) 反応速度定数。
  * `reactant_stoch`: 反応物のストイキオメトリベクトル。
  * `net_stoch`: ネットストイキオメトリベクトル。
  * `param_mapper`: 反応速度定数を `p` ベクトルのパラメータと識別するためのパラメータマッピングファンクタ。

## キーワード引数

  * `scale_rates = true`: ストイキオメトリに従って反応速度定数を再スケーリングするかどうか。
  * `nocopy = false`: `MassActionJump` が入力から `scaled_rates` と `reactant_stoch` をエイリアスできるかどうか。`scale_rates=true` の場合、これらの両方が変更される可能性があることに注意してください。
  * `param_idxs = nothing`: 各反応の速度に対応するパラメータベクトル `JumpProblem.prob.p` のインデックス。

詳細については、チュートリアルとメインドキュメントを参照してください。

## 例

最初の反応として `S + I --> 2I` を速度 β で、2 番目の反応として `I --> R` を速度 ν で持つ SIR モデルは、次のようにエンコードできます。

```julia
p        = (β=1e-4, ν=.01)
u0       = [999, 1, 0]       # (S,I,R)
tspan    = (0.0, 250.0)
rateidxs = [1, 2]           # すなわち [β,ν]
reactant_stoich =
[
  [1 => 1, 2 => 1],         # 1*S と 1*I
  [2 => 1]                  # 1*I
]
net_stoich =
[
  [1 => -1, 2 => 1],        # -1*S と 1*I
  [2 => -1, 3 => 1]         # -1*I と 1*R
]
maj = MassActionJump(reactant_stoich, net_stoich; param_idxs=rateidxs)
prob = DiscreteProblem(u0, tspan, p)
jprob = JumpProblem(prob, Direct(), maj)
```

## 注意事項

  * デフォルトでは、`MassActionJump` を構築する際に反応速度は再スケーリングされます。これは [main docs](https://docs.sciml.ai/JumpProcesses/stable/jump_types/#Defining-a-Mass-Action-Jump) で説明されています。これを無効にするには、キーワード引数 `scale_rates=false` を使用してください。
  * 反応に生成物や反応物がない場合の指定方法については、[main docs](https://docs.sciml.ai/JumpProcesses/stable/jump_types/#Defining-a-Mass-Action-Jump) も参照してください。

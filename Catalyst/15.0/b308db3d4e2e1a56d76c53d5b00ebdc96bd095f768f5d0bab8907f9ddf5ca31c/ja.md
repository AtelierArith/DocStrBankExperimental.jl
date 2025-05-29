```
lat_setu!(sim_struct, sp, lrs::LatticeReactionSystem, u)
```

問題や積分器に対して、入力 `u` で `u` ベクトルを更新します。非格子モデルの場合、これは直接インターフェースを通じて行うことができます（例：`prob[X] = 1.0`）。しかし、`LatticeReactionSystem` ベースの問題や積分器の場合、この関数を代わりに使用する必要があります。

引数:

  * `sim_struct`: 更新したい `u` 値を持つシミュレーション構造。`ODEProblem`、`JumpProblem`、またはこれらのいずれかから派生した積分器のいずれかである必要があります。
  * `sp`: 更新したい値を持つ種。記号形式（例：`X`）またはシンボル（例：`:X`）のいずれかで提供できます。
  * `lrs`: 修正したい構造を生成するために使用された `LatticeReactionSystem`。
  * `u`: 種の新しい値。`ODEProblem`/`JumpProblem` に対する有効な初期入力としても有効な形式で与える必要があります。

例:

```julia
# `LatticeReactionSystem` を準備します。
using Catalyst
rs = @reaction_network begin
    (k1,k2), X1 <--> X2
end
tr = @transport_reaction D X1
lrs = LatticeReactionSystem(rs, [tr], CartesianGrid((2,3)))

# 対応する ODEProblem を準備します。
u0 = [:X1 => [1.0 2.0 3.0; 4.0 5.0 6.0], :X2 => 2.0]
tspan = (0.0, 50.0)
ps = [:k1 => 2.0, :k2 => 1.0, :D => 0.01]
oprob = ODEProblem(lrs, u0, tspan, ps)

# `ODEProblem` を更新します。
lat_setu!(oprob, :X1, lrs, 0.0) # `X1` を格子全体で均等に 0 に設定します。
lat_setu!(oprob, :X2, lrs, [1.0 0.0 0.0; 0.0 0.0 0.0]) # `X2` を一つの頂点で `1.0` に設定し、他は 0 にします。
```

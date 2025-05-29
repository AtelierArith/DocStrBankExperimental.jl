```
lat_getp(sim_struct, p, lrs::LatticeReactionSystem)
```

問題や積分器のために、その `p` 値を取得します。非格子モデルの場合、これは直接インターフェースを通じて行うことができます（例： `prob[p]`）。しかし、`LatticeReactionSystem` ベースの問題や積分器の場合、この関数を代わりに使用する必要があります。出力形式は格子によって異なり（直交格子格子の場合は密な配列、マスクされた格子格子の場合は疎な配列、グラフ格子の場合はベクトル）、この形式はパラメータ初期値を指定するために使用されるものに似ています。

引数:

  * `sim_struct`: 取得したい `p` 値を持つシミュレーション構造。`ODEProblem`、`JumpProblem`、またはこれらのいずれかから派生した積分器のいずれかであることができます。
  * `p`: 更新したい種の値。シンボリック形式（例： `k`）またはシンボル（例： `:k`）のいずれかで提供できます。
  * `lrs`: 修正したい構造を生成するために使用された `LatticeReactionSystem`。

注意:

  * パラメータが空間的に均一であっても、すべての頂点にわたる値を持つ完全な配列が取得されます。

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
u0 = [:X1 => 1.0, :X2 => 2.0]
tspan = (0.0, 50.0)
ps = [:k1 => [1.0 2.0 3.0; 4.0 5.0 6.0], :k2 => 1.0, :D => 0.01]
oprob = ODEProblem(lrs, u0, tspan, ps)

# `ODEProblem` を更新します。
lat_getp(oprob, :k1, lrs) # `k1` の値を取得します。
```

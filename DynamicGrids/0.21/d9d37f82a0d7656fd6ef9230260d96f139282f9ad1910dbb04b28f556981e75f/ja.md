```
Life <: NeighborhoodRule

Life(neighborhood, born=3, survive=(2, 3))
```

ゲーム・オブ・ライフスタイルのセルオートマトンのルール。これは、真剣に最適化されたゲーム・オブ・ライフのルールよりも、セルオートマトンのデモンストレーションです。

セルは、空であり、隣接するセルの数が `born` の数に含まれる場合にアクティブになり、アクティブなセルが隣接するセルの数が `survive` に含まれる場合にアクティブなままになります。

## 例 (CellularAutomata.jlから得たもの)

```julia
using DynamicGrids, Distributions

# `Binomial`を使用して、密度のランダムな真の値を調整します
init = Bool.(rand(Binomial(1, 0.5), 70, 70))
output = REPLOutput(init; tspan=1:100, fps=25, color=:red)

# モーリー
sim!(output, Ruleset(Life(born=[3, 6, 8], survive=[2, 4, 5])))

# 2x2
sim!(output, Ruleset(Life(born=[3, 6], survive=[1, 2, 5])))

# ダイモエバ
init = rand(Bool, 400, 300)
init[:, 100:200] .= 0
output = REPLOutput(init; tspan=1:100, fps=25, color=:blue, style=Braile())
sim!(output, Life(born=(3, 5, 6, 7, 8),  survive=(5, 6, 7, 8)))

## 死亡なし
sim!(output, Life(born=(3,),  survive=(0, 1, 2, 3, 4, 5, 6, 7, 8)))

## 34ライフ
sim!(output, Life(born=(3, 4), survive=(3, 4)))

# 複製者
init = fill(true, 300,300)
init[:, 100:200] .= false
init[10, :] .= 0
output = REPLOutput(init; tspan=1:100, fps=25, color=:yellow)
sim!(output, Life(born=(1, 3, 5, 7),  survive=(1, 3, 5, 7)))
nothing

# 出力

```

![REPL Life](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/life.gif)

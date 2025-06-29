```
Life <: NeighborhoodRule

Life(neighborhood, born=3, survive=(2, 3))
```

Rule for game-of-life style cellular automata. This is a demonstration of Cellular Automata more than a seriously optimised game of life rule.

Cells becomes active if it is empty and the number of neightbors is a number in the `born`, and remains active the cell is active and the number of neightbors is in `survive`.

## Examples (gleaned from CellularAutomata.jl)

```julia
using DynamicGrids, Distributions

# Use `Binomial` to tweak the density random true values
init = Bool.(rand(Binomial(1, 0.5), 70, 70))
output = REPLOutput(init; tspan=1:100, fps=25, color=:red)

# Morley
sim!(output, Ruleset(Life(born=[3, 6, 8], survive=[2, 4, 5])))

# 2x2
sim!(output, Ruleset(Life(born=[3, 6], survive=[1, 2, 5])))

# Dimoeba
init = rand(Bool, 400, 300)
init[:, 100:200] .= 0
output = REPLOutput(init; tspan=1:100, fps=25, color=:blue, style=Braile())
sim!(output, Life(born=(3, 5, 6, 7, 8),  survive=(5, 6, 7, 8)))

## No death
sim!(output, Life(born=(3,),  survive=(0, 1, 2, 3, 4, 5, 6, 7, 8)))

## 34 life
sim!(output, Life(born=(3, 4), survive=(3, 4)))

# Replicator
init = fill(true, 300,300)
init[:, 100:200] .= false
init[10, :] .= 0
output = REPLOutput(init; tspan=1:100, fps=25, color=:yellow)
sim!(output, Life(born=(1, 3, 5, 7),  survive=(1, 3, 5, 7)))
nothing

# output

```

![REPL Life](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/life.gif)

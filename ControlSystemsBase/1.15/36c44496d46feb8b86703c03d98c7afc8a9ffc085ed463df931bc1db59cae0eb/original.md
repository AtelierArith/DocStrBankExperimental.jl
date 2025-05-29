```
feedback(sys1::AbstractStateSpace, sys2::AbstractStateSpace;
         U1=:, Y1=:, U2=:, Y2=:, W1=:, Z1=:, W2=Int[], Z2=Int[],
         Wperm=:, Zperm=:, pos_feedback::Bool=false)
```

*Basic use* `feedback(sys1, sys2)` forms the (negative) feedback interconnection

```julia
           ┌──────────────┐
◄──────────┤     sys1     │◄──── Σ ◄──────
    │      │              │      │
    │      └──────────────┘      -1
    │                            |
    │      ┌──────────────┐      │
    └─────►│     sys2     ├──────┘
           │              │
           └──────────────┘
```

If no second system `sys2` is given, negative identity feedback (`sys2 = 1`) is assumed. The returned closed-loop system will have a state vector comprised of the state of `sys1` followed by the state of `sys2`.

*Advanced use* `feedback` also supports more flexible use according to the figure below

```julia
              ┌──────────────┐
      z1◄─────┤     sys1     │◄──────w1
 ┌─── y1◄─────┤              │◄──────u1 ◄─┐
 │            └──────────────┘            │
 │                                        α
 │            ┌──────────────┐            │
 └──► u2─────►│     sys2     ├───────►y2──┘
      w2─────►│              ├───────►z2
              └──────────────┘
```

  * `U1`, `W1` specify the indices of the input signals of `sys1` corresponding to `u1` and `w1`. `W1` contains the indices of the inputs of `sys1` that are included among the inputs to the returned system, i.e., external inputs.
  * `Y1`, `Z1` specify the indices of the output signals of `sys1` corresponding to `y1` and `z1`. `Z1 contains the indices of the outputs of`sys1` that are included among the outputs of the returned system, i.e., external outputs.
  * `U2`, `W2`, `Y2`, `Z2` specify the corresponding signals of `sys2`. `W2 contains the indices of the inputs of`sys2`that are included among the inputs to the returned system, i.e., external inputs.`Z2`contains the indices of the outputs of`sys2` that are included among the outputs of the returned system, i.e., external outputs.

Specify  `Wperm` and `Zperm` to reorder the inputs (corresponding to [w1; w2]) and outputs (corresponding to [z1; z2]) in the resulting statespace model.

Negative feedback (α = -1) is the default. Specify `pos_feedback=true` for positive feedback (α = 1).

See also `lft`, `starprod`, `sensitivity`, `input_sensitivity`, `output_sensitivity`, `comp_sensitivity`, `input_comp_sensitivity`, `output_comp_sensitivity`, `G_PS`, `G_CS`.

The manual section [From block diagrams to code](https://juliacontrol.github.io/ControlSystems.jl/stable/man/creating_systems/#From-block-diagrams-to-code) contains higher-level instructions on how to use this function. See also [RobustAndOptimalControl.jl: Connections using named signals](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/#Connecting-systems-together) for a higher-level interface.

See Zhou, Doyle, Glover (1996) for similar (somewhat less symmetric) formulas.

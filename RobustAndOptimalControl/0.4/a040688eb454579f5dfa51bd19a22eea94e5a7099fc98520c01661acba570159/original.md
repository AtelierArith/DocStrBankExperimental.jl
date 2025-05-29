```
K, γ, info = glover_mcfarlane_2dof(G::AbstractStateSpace{Continuous}, Tref::AbstractStateSpace{Continuous}, γ = 1.1, ρ = 1.1;
W1 = 1, Wo = I, match_dc = true, kwargs...)
```

Joint design of feedback and feedforward compensators

$$
K = \begin{bmatrix} K_1 & K_2 \end{bmatrix}
$$

```
   ┌──────┐   ┌──────┐        ┌──────┐    ┌─────┐
r  │      │   │      │        │      │    │     │
──►│  Wi  ├──►│  K1  ├───+───►│  W1  ├───►│  G  ├─┐y
   │      │   │      │   │    │      │    │     │ │
   └──────┘   └──────┘   │    └──────┘    └─────┘ │
                         │                        │
                         │    ┌──────┐            │
                         │    │      │            │
                         └────┤  K2  ◄────────────┘
                              │      │
                              └──────┘
```

Where the returned controller `K` takes the measurement vector `[r; y]` (positive feedback),  i.e., it includes all blocks `Wi, K1, K2, W1`. If `match_dc = true`, `Wi` is automatically computed to make sure the static gain matches `Tref` exactly, otherwise `Wi` is set to `I`. The `info` named tuple contains the feedforward filter for inspection (`info.K1 = K1*Wi`).

# Arguments:

  * `G`: Plant model
  * `Tref`: Reference model
  * `γ`: Relative γ
  * `ρ`: Design parameter, typically 1 < ρ < 3. Increase to emphasize model matching at the expense of robustness.
  * `W1`: Pre-compensator for loop shaping.
  * `Wo`: Output selction matrix. If there are more measurements than controlled variables, this matrix let's you select which measurements are to be controlled.
  * `kwargs`: Are sent to [`hinfsynthesize`](@ref).

Ref: Sec. 9.4.3 of Skogestad, "Multivariable Feedback Control: Analysis and Design". The reference contains valuable pointers regarding gain-scheduling implementation of the designed controller as an observer with feedback from estimated states. In order to get anti-windup protection when `W1` contains an integrator, transform `W1` to self-conditioned Hanus form (using [`hanus`](@ref)) and implement the controller like this

```julia
W1h = hanus(W1)             # Perform outside loop

# Each iteration
us = filter(Ks, [r; y])     # filter inputs through info.Ks (filter is a fictive function that applies the transfer function)
u  = filter(W1h, [us; ua])  # filter us and u-actual (after input saturation) through W1h
ua = clamp(u, lower, upper) # Calculate ua for next iteration as the saturated value of u
```

# Example:

```@example
using RobustAndOptimalControl, Plots
P = tf([1, 5], [1, 2, 10]) # Plant
W1 = tf(1,[1, 0]) |> ss    # Loop shaping controller

Tref = tf(1, [1, 1])^2 |> ss # Reference model (preferably of same order as P)

K1dof, γ1, info1 = glover_mcfarlane(ss(P), 1.1; W1)
K2dof, γ2, info2 = glover_mcfarlane_2dof(ss(P), Tref, 1.1, 1.1; W1)

G1 = feedback(P*K1dof)
G2 = info2.Gcl

w = exp10.(LinRange(-2, 2, 200))
bodeplot(info2.K1, w, lab="Feedforward filter")
plot([step(G1, 15), step(G2, 15), step(Tref, 15)], lab=["1-DOF" "2-DOF" "Tref"])
```

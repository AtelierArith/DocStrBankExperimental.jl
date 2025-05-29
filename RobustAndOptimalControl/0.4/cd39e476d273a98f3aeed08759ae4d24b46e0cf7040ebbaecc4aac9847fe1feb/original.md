```
K, γ, info = glover_mcfarlane(G::AbstractStateSpace, γ = 1.1; W1=1, W2=1)
```

Design a controller for `G` that maximizes the stability margin ϵ = 1/γ with normalized coprime factor uncertainty using the method of Glover and McFarlane

```
γ = 1/ϵ = ||[K;I] inv(I-G*K)*inv(M)||∞
G = inv(M + ΔM)*(N + ΔN)
```

γ is given as a relative factor above γmin and must be greater than 1, i.e., if γ = 1.1, the controller will be designed for γ = 1.1*γmin.

We want γmin (which is always ≥ 1) as small as possible, and we usually require that γmin is less than 4, corresponding to 25% allowed coprime uncertainty.

Performance modeling is incorporated in the design by calling `glover_mcfarlane` on the shaped system `Gs = W2*G*W1` and then forming the controller as `K = W1*Ks*W2`. Using this formulation, traditional loop shaping can be done on `Gs = W2*G*W1`. The plant shaping is handled internally if keyword arguments `W1, W2` are used and the returned controller is already scaled. In this case, `Gs` and `Ks` are included in the `info` named tuple for inspection. 

See also [`glover_mcfarlane_2dof`](@ref) to design a feedforward filter as well and [`baltrunc_coprime`](@ref) for controller order reduction. When reducing the order of the calculated controller, reduce the order of `info.Ks` and form `Kr=W1*Ksred*W2`. Verify the robustness using `ncfmargin(info.Gs, Ksred)` as well as `ncfmargin(G, Kr)`.

# Example:

Example 9.3 from the reference below.

```@example GMF
using RobustAndOptimalControl, ControlSystemsBase, Plots, Test
G = tf(200, [10, 1])*tf(1, [0.05, 1])^2     |> ss
Gd = tf(100, [10, 1])                       |> ss
W1 = tf([1, 2], [1, 1e-6])                  |> ss
K, γ, info = glover_mcfarlane(G, 1.1; W1)
@test info.γmin ≈ 2.34 atol=0.005
Gcl = extended_gangoffour(G, K) # Form closed-loop system

fig1 = bodeplot([G, info.Gs, G*K], lab=["G" "" "G scaled" "" "Loop transfer"])
fig2 = bodeplot(Gcl, lab=["S" "KS" "PS" "T"], plotphase=false) # Plot gang of four

fig3 = plot(step(Gd*feedback(1, info.Gs), 3), lab="Initial controller")
plot!(step(Gd*feedback(1, G*K), 3), lab="Robustified")
fig4 = nyquistplot([info.Gs, G*K], ylims=(-2,1), xlims=(-2, 1),
    Ms_circles = 1.5,
    lab = ["Initial controller" "Robustified"],
    title = "Loop transfers with and without robustified controller"
)
plot(fig1, fig2, fig3, fig4)
```

Example of controller reduction: The order of the controller designed above can be reduced maintaining at least 2/3 of the robustness margin like this

```@example GMF
e,_ = ncfmargin(info.Gs, info.Ks)
Kr, hs, infor = baltrunc_coprime(info.Ks, n=info.Ks.nx)
n = findlast(RobustAndOptimalControl.error_bound(hs) .> 2e/3) # 2/3 e sets the robustness margin
Ksr, hs, infor = baltrunc_coprime(info.Ks; n)
@test ncfmargin(info.Gs, Ksr)[1] >= 2/3 * e
Kr = W1*Ksr
bodeplot([G*K, G*Kr], lab=["L original" "" "L Reduced" ""])
```

This gives a final controller `Kr` of order 3 instead of order 5, but a very similar robustness margin. You may also call

```@example GMF
controller_reduction_plot(info.Gs, info.Ks)
```

to help you select the controller order.

Ref: Sec 9.4.1 of Skogestad, "Multivariable Feedback Control: Analysis and Design"

# Extended help

Skogestad gives the following general advice:

1. Scale the plant outputs and inputs. This is very important for most design  procedures and is sometimes forgotten. In general, scaling improves the  conditioning of the design problem, it enables meaningful analysis to be made  of the robustness properties of the feedback system in the frequency domain,  and for loop-shaping it can simplify the selection of weights. There are a variety  of methods available including normalization with respect to the magnitude of  the maximum or average value of the signal in question. If one is to go straight to a design the following variation has  proved useful in practice:

      * The outputs are scaled such that equal magnitudes of cross-coupling into each   of the outputs is equally undesirable.
      * Each input is scaled by a given percentage (say 10%) of its expected range   of operation. That is, the inputs are scaled to reflect the relative actuator   capabilities.
2. Order the inputs and outputs so that the plant is as diagonal as possible. The  relative gain array [`relative_gain_array`](@ref) can be useful here. The purpose of this pseudo-diagonalization  is to ease the design of the pre- and post-compensators which, for simplicity, will  be chosen to be diagonal.

    Next, we discuss the selection of weights to obtain the shaped plant $G_s = W_2 G W_1$  where $W_1 = W_p W_a W_g$
3. Select the elements of diagonal pre- and post-compensators $W_p$ and $W_2$ so that  the singular values of $W_2 G W_p$ are desirable. This would normally mean high  gain at low frequencies, roll-off rates of approximately 20 dB/decade (a slope of  about 1) at the desired bandwidth(s), with higher rates at high frequencies. Some  trial and error is involved here. $W_2$ is usually chosen as a constant, reflecting the  relative importance of the outputs to be controlled and the other measurements  being fed back to the controller. For example, if there are feedback measurements  of two outputs to be controlled and a velocity signal, then $W_2$ might be chosen  to be `diag([1, 1, 0.1])`, where 0.1 is in the velocity signal channel. $W_p$ contains the  dynamic shaping. Integral action, for low frequency performance; phase-advance  for reducing the roll-off rates at crossover, and phase-lag to increase the roll-off  rates at high frequencies should all be placed in $W_p$ if desired. The weights should  be chosen so that no unstable hidden modes are created in $G_s$.
4. Optional: Introduce an additional gain matrix $W_g$ cascaded with $W_a$ to provide  control over actuator usage. $W_g$ is diagonal and is adjusted so that actuator rate  limits are not exceeded for reference demands and typical disturbances on the  scaled plant outputs. This requires some trial and error.
5. Robustly stabilize the shaped plant $G_s = W_2 G W_1$ , where $W_1 = W_p W_a W_g$,  using `glover_mcfarlane`. First, the maximum stability  margin $ϵ_{max} = 1/γ_{min}$ is calculated. If the margin is too small, $ϵmax < 0.25$, then go back and modify the weights. Otherwise, a γ-suboptimal controller is synthesized. There is usually no advantage to be gained by using the optimal controller. When $ϵ_{max}$ > 0.25  (respectively $γ_{min}$ < 4) the design is usually successful. In this case, at least  25% coprime factor uncertainty is allowed, and we also find that the shape of the  open-loop singular values will not have changed much after robust stabilization.  A small value of ϵmax indicates that the chosen singular value loop-shapes are  incompatible with robust stability requirements. That the loop-shapes do not  change much following robust stabilization if γ is small (ϵ large), is justified  theoretically in McFarlane and Glover (1990).
6. Analyze the design and if all the specifications are not met make further  modifications to the weights.
7. Implement the controller. The configuration shown in below has been found  useful when compared with the conventional set up. This is because  the references do not directly excite the dynamics of $K$, which can result in large amounts of overshoot (classical derivative kick). The constant prefilter ensures a steady-state gain of 1 between r and y, assuming integral action in $W_1$ or $G$ (note, the K returned by this function has opposite sign compared to that of Skogestad, so we use negative feedback here).

Anti-windup can be added to $W_1$ but putting $W_1$ on Hanus form after the synthesis, see [`hanus`](@ref).

```
       ┌─────────┐      ┌────────┐      ┌────────┐
    r  │         │    us│        │  u   │        │  y
   ───►│(K*W2)(0)├──+──►│   W1   ├─────►│   G    ├────┬──►
       │         │  │-  │        │      │        │    │
       └─────────┘  │   └────────┘      └────────┘    │
                    │                                 │
                    │                                 │
                    │   ┌────────┐      ┌────────┐    │
                    │   │        │  ys  │        │    │
                    └───┤   K    │◄─────┤   W2   │◄───┘
                        │        │      │        │
                        └────────┘      └────────┘
```

Keywords: `nfcsyn`, `coprimeunc`

```
G = LQGProblem(sys::ExtendedStateSpace, Q1, Q2, R1, R2; qQ=0, qR=0, SQ=nothing, SR=nothing)
```

Return an LQG object that describes the closed control loop around the process `sys=ss(A,B,C,D)` where the controller is of LQG-type. The controller is specified by weight matrices `Q1,Q2` that penalizes state deviations and control signal variance respectively, and covariance matrices `R1,R2` which specify state drift and measurement covariance respectively.

`sys` is an extended statespace object where the upper channel corresponds to disturbances to performance variables (w→z), and the lower channel corresponds to inputs to outputs (u→y), such that `lft(sys, K)` forms the closed-loop transfer function from external inputs/disturbances to performance variables. 

`qQ` and `qR` can be set to incorporate loop-transfer recovery, i.e.,

```julia
L = lqr(A, B, Q1+qQ*C'C, Q2)
K = kalman(A, C, R1+qR*B*B', R2)
```

Increasing `qQ` will add more cost in output direction, e.g., encouraging the use of cheap control, while increasing `qR` adds fictious dynamics noise, makes the observer faster in the direction we control.

# Example

In this example we will control a MIMO system with one unstable pole and one unstable zero. When the system has both unstable zeros and poles, there are fundamental limitations on performance. The unstable zero is in this case faster than the unstable pole, so the system is controllable. For good performance, we want as large separation between the unstable zero dynamics and the unstable poles as possible. 

```julia
s = tf("s")
P = [1/(s+1) 2/(s+2); 1/(s+3) 1/(s-1)]
sys = ExtendedStateSpace(ss(P)) # Controlled outputs same as measured outputs and state noise affects at inputs only. 
eye(n) = Matrix{Float64}(I,n,n) # For convinience

qQ = 0
qR = 0
Q1 = 10eye(2)
Q2 = 1eye(2)
R1 = 1eye(2)
R2 = 1eye(2)

G = LQGProblem(sys, Q1, Q2, R1, R2, qQ=qQ, qR=qR)

T = comp_sensitivity(G)
S = sensitivity(G)
Gcl = closedloop(G)*static_gain_compensation(G)
plot(
    sigmaplot([S,T, Gcl],exp10.(range(-3, stop=3, length=1000)), lab=["S" "T" "Gry"]),
    plot(step(Gcl, 5))
)
```

# Extended help

Several functions are defined for instances of `LQGProblem`

  * [`closedloop`](@ref)
  * [`extended_controller`](@ref)
  * [`ff_controller`](@ref)
  * [`gangoffour`](@ref)
  * [`G_CS`](@ref)
  * [`G_PS`](@ref)
  * [`input_comp_sensitivity`](@ref)
  * [`input_sensitivity`](@ref)
  * [`output_comp_sensitivity`](@ref)
  * [`output_sensitivity`](@ref)
  * [`system_mapping`](@ref)
  * [`performance_mapping`](@ref)
  * [`static_gain_compensation`](@ref)
  * [`gangoffourplot`](@ref)
  * [`kalman`](@ref)
  * [`lft`](@ref)
  * [`lqr`](@ref)
  * [`observer_controller`](@ref)

A video tutorial on how to use the LQG interface is available [here](https://youtu.be/NuAxN1mGCPs)

## Introduction of references

The most principled way of introducing references is to add references as measured inputs to the extended statespace model, and to let the performance output `z` be the differences between the references and the outputs for which references are provided. 

A less cumbersome way is not not consider references when constructing the `LQGProblem`, and instead pass the `z` keyword arugment to [`extended_controller`](@ref) in order to obtain a closed-loop system from state references to controlled outputs, and use some form of inverse of the DC gain of this system (or one of its subsystems) to pre-compensate the reference input.

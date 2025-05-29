```
InternalModel(model::SimModel; i_ym=1:model.ny, stoch_ym=ss(I,I,I,I,model.Ts))
```

Construct an internal model estimator based on `model` ([`LinModel`](@ref) or [`NonLinModel`](@ref)).

`i_ym` provides the `model` output indices that are measured $\mathbf{y^m}$, the rest are  unmeasured $\mathbf{y^u}$. `model` evaluates the deterministic predictions  $\mathbf{ŷ_d}$, and `stoch_ym`, the stochastic predictions of the measured outputs  $\mathbf{ŷ_s^m}$ (the unmeasured ones being $\mathbf{ŷ_s^u=0}$). The predicted outputs sum both values : $\mathbf{ŷ = ŷ_d + ŷ_s}$. See the Extended Help for more details. This estimator is allocation-free is `model` simulations do not allocate.

!!! warning
    `InternalModel` estimator does not work if `model` is integrating or unstable. The  constructor verifies these aspects for `LinModel` but not for `NonLinModel`. Uses any  other state estimator in such cases.


# Examples

```jldoctest
julia> estim = InternalModel(LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5), i_ym=[2])
InternalModel estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u
 2 estimated states x̂
 1 measured outputs ym
 1 unmeasured outputs yu
 0 measured disturbances d
```

# Extended Help

!!! details "Extended Help"
    `stoch_ym` is a `TransferFunction` or `StateSpace` object that models disturbances on $\mathbf{y^m}$. Its input is a hypothetical zero mean white noise vector. `stoch_ym`  supposes 1 integrator per measured outputs by default, assuming that the current stochastic estimate $\mathbf{ŷ_s^m}(k) = \mathbf{y^m}(k) - \mathbf{ŷ_d^m}(k)$ is constant in the  future. This is the dynamic matrix control (DMC) strategy, which is simple but sometimes too aggressive. Additional poles and zeros in `stoch_ym` can mitigate this. The following block diagram summarizes the internal model structure.

    ![block diagram of the internal model structure](../assets/imc.svg)


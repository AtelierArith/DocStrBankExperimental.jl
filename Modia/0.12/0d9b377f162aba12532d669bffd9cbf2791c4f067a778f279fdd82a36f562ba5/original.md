```
(A, finalStates) = linearize!(instantiatedModel [, algorithm];
                              stopTime = 0.0,
                              analytic = false,
                              <all other keyword arguments of simulate!>)
```

Simulate until `stopTime` and linearize `instantiatedModel` at `finalStates`. The names of the state vector can be inquired by `get_xNames(instantiatedModel)`.

By default, linearization is performed numerically with a central finite difference approximation using package [FiniteDiff](https://github.com/JuliaDiff/FiniteDiff.jl). When setting `analytic = true`, linearization is preformed analytically with package [ForwardDiff](https://github.com/JuliaDiff/ForwardDiff.jl), so is computed by symbolically differentiating the model. `ForwardDiff` might not be compatible with some floating point types, such as `Measurements` and Julia triggers an error that some overloaded operations are ambiguous. So `analytic=true` will not work in such cases.

Analytic linearization returns matrix `A` in full precision whereas numeric linearization returns `A` in reduced precision (if FloatType = Float64, analytic linearization results in about 15 correct digits and numeric linearization in about 10 correct digits in the result). You can improve this situation, by using a larger `FloatType` for `instantiatedModel`, in case this is critical (see example below).

# Output arguments

  * `A::Matrix`: Matrix A of the linear ODE: $\Delta \dot{x} = A*\Delta x$.
  * `finalStates::Vector`: Linearization point.

# Example

```julia
using Modia
using DoubleFloats
using Measurements

FirstOrder = Model(
    T = 0.4 ± 0.04,
    x = Var(init = 0.9 ± 0.09),
    equations = :[u = inputSignal(time/u"s"),
                  T * der(x) + x = u]
)

firstOrder1 = @instantiateModel(FirstOrder, FloatType = Measurement{Float64})

# Standard precision
(A1, finalStates1) = linearize!(firstOrder1)

# Higher precision
firstOrder2 = InstantiatedModel{Measurement{Double64}}(firstOrder1)
(A2, finalStates2) = linearize!(firstOrder2)

# Show results with 15 digits (default print with Measurements shows 3 digits)
println(IOContext(stdout, :error_digits=>15), "A1 = ", A1)
println(IOContext(stdout, :error_digits=>15), "A2 = ", A2)
```

```
MeasurementModel
```

`MeasurementModel` is an abstract type representing a vector function of a vector input with correlated uncertainties.  A `MeasurementModel` is responsible for calculating vector function outputs and the associated Jacobian matrix both evaluated at the input values.

To emphasize that a MeasurementModel represents a vector function that takes an UncertainValues object representing the input values into an UncertainValues object representing the output values, the function operator has been overloaded:

```
(mm::MeasurementModel)(uvs::UncertainValues)::UncertainValues
```

or

```
(mm::MeasurementModel)(uvs::Dict{<:Label, UncertainValue})::UncertainValues
```

This helps you to think of a MeasurementModel as the equivalent of a function for UncertainValues.

Furthermore, you can compose / pipe / chain `MeasurementModel`s together to implement a multi-step calculation using the ∘ operator.  If `mm1` and `mm2` are `MeasurementModel`s such that the inputs for `mm2` come from `mm1` (and the original inputs) then:

```
(mm2 ∘ mm1)(inputs) = mm2(mm1(inputs))
```

Equivalently, if `mm3` and `mm4` both take the same inputs they may be computed in parallel using:

```
(mm3 | mm4)(inputs) = cat(mm3(inputs), mm4(inputs))
```

You can combine `∘` and `|` together like this:

```
(mm2 ∘ (mm3 | mm4) ∘ mm1)(inputs) = mm2(cat(mm3(mm1(inputs)),mm4(mm1(inputs))))
```

which first computes `o1=mm1(inputs)` then computes `o3=mm3(inputs+o1)` and `o4=mm4(inputs+o1)` finally  computes `mm2(inputs+o1+o3+o4)`.

Composing `MeasurementModel`s is where the magic occurs. For a complex measurement model, it may not be feasible/possible to calculate an analytical form of the partial derivative. However, if the model can be broken into a series of smaller composable steps for which the analytical partial derivative can be calculated, the steps can be combined to build the full model.  Of course this isn't magic, it results from this property of Jacobians:

$\mathbf{J}_{g(f(x))} |_x = \mathbf{J}_g(y) |_{f(x)} \mathbf{J}_{f(x)} |_x$

To use this framework on your measurement model, you must implement the function `compute(...)` for `YourMeasurementModel`.

```
compute(mm::YourMeasurementModel, inputs::LabeledValues, withJac::Boolean)::MMResult
```

where

```
MMResult = Tuple{LabeledValues, Union{Missing,AbstractMatrix{Float64}}}
```

The function `compute(...)` is responsible for computing the models output values and the Jacobian of the output values with respect to the input values.  The Jacobian is a matrix with one row per output value and one column per input value. The contents of the r,c-th element is the partial derivative of the r-th output value with respect to the c-th input value.

`MMResult` represents the function output values (`LabeledValues`) and the Jacobian as an `AbstractMatrix{Float64}`.  To optimize the `compute(...)` function when used to simply compute the vector valued function, the Jacobian must calculated only when `withJac=true`.  If `withJac=false` then returning 'missing' for the Jacobian is encouraged.  This facilates efficiency when using 'compute(...)' in situations like Monte Carlo propagation (using `mcpropagate(...)`) where it is wasteful to compute the Jacobian but you'd otherwise like to use identical code to compute the function values.

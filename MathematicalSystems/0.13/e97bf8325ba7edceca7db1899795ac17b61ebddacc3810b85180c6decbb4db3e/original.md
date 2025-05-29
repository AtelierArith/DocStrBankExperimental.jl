```
discretize(system::AbstractContinuousSystem, ΔT::Real,
           algorithm::AbstractDiscretizationAlgorithm=ExactDiscretization(),
           constructor=_default_complementary_constructor(system))
```

Discretization of a `isaffine` `AbstractContinuousSystem` to a `AbstractDiscreteSystem` with sampling time `ΔT` using the discretization method `algorithm`.

### Input

  * `system`      – an affine continuous system
  * `ΔT`          – sampling time
  * `algorithm`   – (optional, default: `ExactDiscretization()`) discretization algorithm
  * `constructor` – (optional, default: `_default_complementary_constructor(system)`) construction method

### Output

Returns a discretization of the input system `system` with discretization method `algorithm` and sampling time `ΔT`.

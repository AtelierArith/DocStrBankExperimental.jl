```julia
GTM(; stm, name)

```

NASA's Generic Transport Model can be approximated (near select flight conditions) as a polynomial model. Here, `GTM` is a `ModelingToolkit.ODESystem` which provides publicly available polynomial approximations for GTM longitudinal flight dynamics.

# Extended Help

## Initial Conditions

The default initial conditions are one trim condition. Two trim conditions for these polynomial-approximated dynamics are shown below.

```julia
trim₁ = [[29.6, deg2rad(9), 0.0, deg2rad(9)],   [deg2rad(0.68), 12.7]]
trim₂ = [[25.0, deg2rad(18), 0.0, deg2rad(18)], [deg2rad(-7.2), 59]]
```

## Usage

```julia
model = GTM()
```

## References:

  * [Chakraborty et al](https://www.sciencedirect.com/science/article/abs/pii/S0967066110002595)
  * [Joe Carpinelli](https://github.com/cadojo/Replicated-ROA-Analysis)

```
CompositeModel(components;
gas = BasicIdeal,
liquid = RackettLiquid,
saturation = LeeKeslerSat,
gas_userlocations = String[],
liquid_userlocations = String[],
saturation_userlocations = String[],
mapping = nothing,
reference_state = nothing,
verbose = false)
```

Model that holds representations of fluid (and/or solid) that aren't evaluated using the helmholtz energy-based approach used in the rest of the library.

It contains a "fluid" and a "solid" field. there are three available representations for a fluid:

  * a helmholtz-based EoS
  * Fluid Correlations, consisting in a gas model, a correlation for obtaining the saturation pressure, and a liquid model. both gas and liquid models can optionally be helmholtz models too, but correlations for saturated liquid and vapour are also allowed.
  * Activity models, consisting of a liquid activity and a model for the fluid. the fluid model can be a helmholtz-based model, or another `CompositeModel` containing correlations.

When the solid field is specified, some properties (like `volume`) start taking in account the solid phase in their calculations. optionally, there are other models that provide specific correlations for SLE equilibria (like `SolidHfus`)

## Examples:

  * Saturation pressure calculated using Correlations:

```julia-repl
#rackett correlation for liquids, DIPPR 101 correlation for the saturation pressure, ideal gas for the vapour volume
julia> model = CompositeModel(["water"],liquid = RackettLiquid,saturation = DIPPR101Sat,gas = BasicIdeal)
Composite Model (Correlation-Based) with 1 component:
 Gas Model: BasicIdeal()
 Liquid Model: RackettLiquid("water")
 Saturation Model: DIPPR101Sat("water")

julia> saturation_pressure(model,373.15)
(101260.56298096628, 1.8234039042643886e-5, 0.030639190960720403)
```

  * Bubble Pressure, calculated using fluid correlations and a Raoult solver:

```julia-repl
julia> model = CompositeModel(["octane","heptane"],liquid = RackettLiquid,saturation = DIPPR101Sat,gas = BasicIdeal)
Composite Model (Correlation-Based) with 2 components:
 Gas Model: BasicIdeal()
 Liquid Model: RackettLiquid("octane", "heptane")
 Saturation Model: DIPPR101Sat("octane", "heptane")

julia> bubble_pressure(model,300.15,[0.9,0.1])
(2552.3661540464022, 0.00015684158726046333, 0.9777538974501402, [0.7376170278676232, 0.2623829721323768])
```

  * Bubble Pressure, using an Activity Model along with another model for fluid properties:

```julia-repl
#using a helmholtz-based fluid
julia> model = CompositeModel(["octane","heptane"],liquid = UNIFAC,fluid = PR)
Composite Model (γ-ϕ) with 2 components:
 Activity Model: UNIFAC{PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}}("octane", "heptane")
 Fluid Model: PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}("octane", "heptane")

julia> bubble_pressure(model,300.15,[0.9,0.1])
(2694.150594740186, 0.00016898441224336215, 0.9239727973658585, [0.7407077952279438, 0.2592922047720562])

#using a correlation-based fluid
julia> fluidmodel = CompositeModel(["octane","heptane"],liquid = RackettLiquid,saturation = DIPPR101Sat,gas = BasicIdeal);
model2 = CompositeModel(["octane","heptane"],liquid = UNIFAC, fluid = fluidmodel)
Composite Model (γ-ϕ) with 2 components:
 Activity Model: UNIFAC{PR{BasicIdeal, PRAlpha, NoTranslation, vdW1fRule}}("octane", "heptane")
 Fluid Model: FluidCorrelation{BasicIdeal, RackettLiquid, DIPPR101Sat}("octane", "heptane")

julia> bubble_pressure(model2,300.15,[0.9,0.1])
(2551.6008524130893, 0.00015684158726046333, 0.9780471551726359, [0.7378273929683233, 0.2621726070316766])
```

```
make_compute_exp_tendency(model::PlantHydraulicsModel, _)
```

A function which creates the compute*exp*tendency! function for the PlantHydraulicsModel. The compute*exp*tendency! function must comply with a rhs function of SciMLBase.jl.

Below, `fa` denotes a flux multiplied by the relevant cross section (per unit area ground, or area index, AI). The tendency for the ith compartment can be written then as: ∂ϑ[i]/∂t = 1/(AI*dz)[fa[i]-fa[i+1]).

Note that if the area_index is zero because no plant is present, AIdz is zero, and the fluxes `fa` appearing in the numerator are zero because they are scaled by AI.

To prevent dividing by zero, we change AI/(AI x dz)" to "AI/max(AI x dz, eps(FT))"

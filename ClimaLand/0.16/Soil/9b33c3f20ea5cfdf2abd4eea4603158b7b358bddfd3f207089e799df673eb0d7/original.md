```
boundary_var_types(::Soil.EnergyHydrology{FT}, ::AbstractEnergyHydrologyBC, ::ClimaLand.AbstractBoundary) where {FT}
```

The list of domain names for additional variables added to the EnergyHydrology model auxiliary state, which defaults to adding storage for the  boundary flux field.

Because we supply boundary conditions for water and heat, we found it convenient to have these stored as a NamedTuple under the names `top_bc` and `bottom_bc`.

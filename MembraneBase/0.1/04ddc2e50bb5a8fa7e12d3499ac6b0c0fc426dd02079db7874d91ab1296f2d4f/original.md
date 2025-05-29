```
mass_sorbed(isotherm::IsothermData, polymer_mass_g::Number, component=:)
```

Get mass (in **g**) of penetrant sorbed into the polymer phase, given the mass (in **g**) of the polymer.

!!! note
    If no component is specified in a multicomponent isotherm, a `vector` of masses is returned, **not** the total mass sorbed.


!!! warning
    *The mass of the polymer* in this case means the mass of the polymer *only*. Not the mass of the polymer phase. In most cases, this distinction is insignificant, however in very highly sorbing polymers, this difference can cause significant error if not considered.


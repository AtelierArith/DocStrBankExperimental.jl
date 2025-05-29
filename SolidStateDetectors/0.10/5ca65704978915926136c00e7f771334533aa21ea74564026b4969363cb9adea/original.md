```
add_fano_noise(E_dep::RealQuantity, E_ionisation::RealQuantity, f_fano::Real)::RealQuantity
```

Adds Fano noise to an energy deposition `E_dep`, assuming a detector material ionisation energy `E_ionisation` and a Fano factor `f_fano`.

## Arguments

  * `E_dep::RealQuantity`: Energy deposited in a semiconductor material.
  * `E_ionisation`: Energy needed to create one electron-hole-pair in the semiconductor material.
  * `f_fano`: Fano factor of the material.

## Example

```julia
add_fano_noise(100u"keV", 2.95u"eV", 0.129)
```

Some material properties are stored in `SolidStateDetectors.material_properties` and can be used here:

```julia
material = SolidStateDetectors.material_properties[:HPGe]
add_fano_noise(100u"keV", material.E_ionisation, material.f_fano)
```

!!! note
    Using values with units for `E_dep` or `E_ionisation` requires the package [Unitful.jl](https://github.com/PainterQubits/Unitful.jl).


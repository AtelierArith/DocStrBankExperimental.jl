```
abstract type MoleGas{M,μ,Tμ,k,Tk} <: AbstractMole{M} end
```

Molecular gas susbtance specified by molarmass `M` and Sutherland constants `μ,Tμ,k,Tk`. Induces additional dervived values if applicable `wavenumber`, `wavelength`, `frequency`, `vibration`, and inherited constants associated with the `AbstractMole` values.

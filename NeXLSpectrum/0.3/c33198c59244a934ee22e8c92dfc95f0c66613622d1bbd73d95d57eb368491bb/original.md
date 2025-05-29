```
NeXLCore.energy(ch::Integer, sc::EnergyScale)
NeXLCore.energy(ch::Int, spec::Spectrum)
NeXLCore.energy(ch::Int, det::EDSDetector)
```

Returns the energy (in eV) for the low energy side of the bin representing the ch-th channel.

Example:

```
les = LinearEnergyScale(3.0, 10.1)
energy(101,lsc) == 10.1*101 + 3.0
energy(101,lsc) - energy(100,lsc) == 10.1
pes = PolyEnergyScale([ 3.0, 10.1, 0.001])
energy(101,pes) ==  3.0 + 10.0*101 + 0.001*101^2
```

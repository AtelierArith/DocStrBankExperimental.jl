```
OnePhotonView{T} <: AbstractVector{T}
```

Structure for viewing onephoton excitations in waveguides of the form $W^\dagger(\xi) |0 \rangle = \int_{t_0}^{t_{end}} dt  \xi(t) w_{\mathrm{i}}^\dagger(t) |\emptyset \rangle$ where $i$ is the index of the waveguide. See [`onephoton`](@ref) on how to create onephoton wavepackets and [`view_waveguide`](@ref) on how to index when there are multiple systems.

# Examples

```@example onephotonview
using QuantumOptics;
times = 0:1:10;
bw = WaveguideBasis(1,times);
ψ1 = onephoton(bw,x->1,norm=false);
OnePhotonView(ψ1) == ones(length(times))
```

```@example onephotonview
bc = FockBasis(2);
ψ1Cavity = fockstate(bc,2,norm=false) ⊗ ψ1;
OnePhotonView(ψCavity,[3,:]) == ones(length(times))
```

```@example onephotonview
bw =  WaveguideBasis(1,3,times);
ψ2 = onephoton(bw,2,x->1,norm=false)
OnePhotonView(ψ,2) == ones(length(times))
```

```@example onephotonview
ψ2Cavity = fockstate(bc,2) ⊗ ψ2;
OnePhotonView(ψ2Cavity,2,[3,:]) == ones(length(times))
```

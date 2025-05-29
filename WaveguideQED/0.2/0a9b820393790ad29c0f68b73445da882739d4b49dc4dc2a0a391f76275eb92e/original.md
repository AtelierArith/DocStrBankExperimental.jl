Create a onephoton wavepacket in waveguide of the form $W^\dagger(\xi) |0 \rangle = \int_{t_0}^{t_{end}} dt  \xi(t) w_{\mathrm{i}}^\dagger(t) |\emptyset \rangle = \sum_{k}$ where $i$ is the index of the waveguide and return it as a `Ket`. See also [`WaveguideBasis`](@ref) and [`OnePhotonView`](@ref) for how to view the state. 

# Examples

```@example onewaveguide
dt = 1
times = 1:dt:10;
bw = WaveguideBasis(1,times);
ψ = onephoton(bw,x->dt,norm=false);
OnePhotonView(ψ) == ones(length(times))
```

```@example onewaveguide
vec = collect(1:1:10);
ψ = onephoton(bw,vec);
OnePhotonView(ψ) == vec
```

```@example onewaveguide
bw = WaveguideBasis(1,3,times);
ψ = onephoton(bw,2,x->dt);
OnePhotonView(ψ,2) == ones(length(times))
```

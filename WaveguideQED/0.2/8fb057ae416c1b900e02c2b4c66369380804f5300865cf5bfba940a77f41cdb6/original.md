```
TwophotonView{T} <: AbstractMatrix{T}
```

Structure for viewing twophoton state of the form $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$ where $i$ and $j$ are the indeces of the waveguide as matrix. See also [`twophoton`](@ref) and [`view_waveguide`](@ref).

# Examples

Basic viewing:

```@example twophotview
using LinearAlgebra; #hide
times = 1:1:10;
bw = WaveguideBasis(2,times);
ψ = twophoton(bw,(t1,t2)->1,norm=false);
ψview = TwoPhotonView(ψ);
ψview == ones((length(times),length(times)))
```

Viewing state combined with other basis:

```@example twophotview
using QuantumOptics;
bc = FockBasis(2);
ψcombined = fockstate(bc,2) ⊗ ψ;
ψview = TwoPhotonView(ψcombined,[3,:]);
ψview == ones((length(times),length(times)))
```

Viewing twophoton state in waveguide 2 with multiple waveguides

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,2,(t1,t2)->1,norm=false);
ψview = TwoPhotonView(ψ,2);
ψview == ones((length(times),length(times)))
```

Viewing twophoton state in waveguide 2 with multiple waveguides combined with other basis:

```@example twophotview
ψcombined = fockstate(bc,2) ⊗ ψ;
ψview = TwoPhotonView(ψcombined,2,[3,:]);
ψview == ones((length(times),length(times)))
```

Viewing twophotons across waveguide 1 and 2

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,1,2,(t1,t2)->1,norm=false);
ψview = TwoPhotonView(ψ,1,2);
ψview == ones((length(times),length(times)))
```

Viewing twophotons across waveguide 1 and 2 combined with other basis:

```@example twophotview
ψcombined = fockstate(bc,2) ⊗ ψ;
ψview = TwoPhotonView(ψcombined,1,2,[3,:]);
ψview == ones((length(times),length(times)))
```

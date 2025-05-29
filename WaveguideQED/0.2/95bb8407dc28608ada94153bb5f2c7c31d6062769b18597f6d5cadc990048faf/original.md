Create a twophoton wavepacket of the form $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$ where $i$ and $j$ are the indeces of the waveguide and return it as a `Ket`.

See also [`WaveguideBasis`](@ref) and [`TwoPhotonView`](@ref) for how to view the state. 

#Examples  Creating twophoton state with only one waveguide (using a function):

```@example twophotview
using LinearAlgebra; #hide
times = 1:1:10;
bw = WaveguideBasis(2,times);
ψ = twophoton(bw,(t1,t2)->1,norm=false);
ψview = TwoPhotonView(ψ);
ψview == ones((length(times),length(times)))

ψ = twophoton(bw,(t1,t2,arg1)->arg1,123,norm=false);
ψview = TwoPhotonView(ψ);
ψview == 123*ones((length(times),length(times)))

```

Creating twophoton state with only one waveguide (using a matrix):

```@example twophotview
ψ = twophoton(bw,ones((length(times),length(times))),norm=false);
ψview = TwoPhotonView(ψ);
ψview == ones((length(times),length(times)))
```

Creating twophoton state in waveguide 2 with multiple waveguides

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,2,(t1,t2)->1,norm=false);
```

Creating twophoton state across waveguide 1 and 2

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,1,2,(t1,t2)->1,norm=false);
```

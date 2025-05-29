```
view_waveguide(ψ::ket)
view_waveguide(ψ::ket,index)
```

View the Waveguide state given a state ψ containing a WaveguideBasis by returning `view(reshape(ψ.data,Tuple(ψ.basis.shape)),index...)`. If no index is provided the ground state is returned. The index provided should be of the form `[:,i,j]` where `(:)` is at the location of the WaveguideBasis and i and j are indeces of other basises. See example: 

```@example vw
using QuantumOptics;
times=0:1:10;
bw = WaveguideBasis(1,times);
bc = FockBasis(2);
ψ_waveguide = Ket(bw,ones(length(times)));
ψ_total = ψ_waveguide ⊗ fockstate(bc,0) ⊗ fockstate(bc,0);
ψ_view = view_waveguide(ψ_total);
ψ_view_index = view_waveguide(ψ_total,[:,1,1]);
ψ_view==ψ_view_index
```

```@example vw
ψ_total = ψ_waveguide ⊗ fockstate(bc,2) ⊗ fockstate(bc,1);
view_waveguide(ψ_total,[:,3,2]) == ones(length(times))
true
```

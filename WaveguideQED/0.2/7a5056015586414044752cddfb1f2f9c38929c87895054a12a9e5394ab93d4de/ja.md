```
view_waveguide(ψ::ket)
view_waveguide(ψ::ket,index)
```

波導基底を含む状態 ψ に対して波導状態を表示します。`view(reshape(ψ.data,Tuple(ψ.basis.shape)),index...)` を返します。インデックスが提供されない場合は基底状態が返されます。提供されるインデックスは `[:,i,j]` の形式である必要があり、ここで `(:)` は WaveguideBasis の位置で、i と j は他の基底のインデックスです。例を参照してください:

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

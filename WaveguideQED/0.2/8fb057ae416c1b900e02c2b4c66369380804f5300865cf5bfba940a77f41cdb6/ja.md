```
TwophotonView{T} <: AbstractMatrix{T}
```

二光子状態を表示するための構造体で、形式は $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$ であり、$i$ と $j$ は行列としての波導のインデックスです。 [`twophoton`](@ref) および [`view_waveguide`](@ref) も参照してください。

# 例

基本的な表示:

```@example twophotview
using LinearAlgebra; #hide
times = 1:1:10;
bw = WaveguideBasis(2,times);
ψ = twophoton(bw,(t1,t2)->1,norm=false);
ψview = TwoPhotonView(ψ);
ψview == ones((length(times),length(times)))
```

他の基底と組み合わせた状態の表示:

```@example twophotview
using QuantumOptics;
bc = FockBasis(2);
ψcombined = fockstate(bc,2) ⊗ ψ;
ψview = TwoPhotonView(ψcombined,[3,:]);
ψview == ones((length(times),length(times)))
```

複数の波導を持つ波導2の二光子状態の表示:

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,2,(t1,t2)->1,norm=false);
ψview = TwoPhotonView(ψ,2);
ψview == ones((length(times),length(times)))
```

他の基底と組み合わせた複数の波導を持つ波導2の二光子状態の表示:

```@example twophotview
ψcombined = fockstate(bc,2) ⊗ ψ;
ψview = TwoPhotonView(ψcombined,2,[3,:]);
ψview == ones((length(times),length(times)))
```

波導1と2にまたがる二光子の表示:

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,1,2,(t1,t2)->1,norm=false);
ψview = TwoPhotonView(ψ,1,2);
ψview == ones((length(times),length(times)))
```

他の基底と組み合わせた波導1と2にまたがる二光子の表示:

```@example twophotview
ψcombined = fockstate(bc,2) ⊗ ψ;
ψview = TwoPhotonView(ψcombined,1,2,[3,:]);
ψview == ones((length(times),length(times)))
```

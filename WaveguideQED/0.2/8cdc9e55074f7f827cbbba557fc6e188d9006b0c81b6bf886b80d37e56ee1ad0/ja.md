```
OnePhotonView{T} <: AbstractVector{T}
```

波導における一光子励起を表示するための構造で、$W^\dagger(\xi) |0 \rangle = \int_{t_0}^{t_{end}} dt  \xi(t) w_{\mathrm{i}}^\dagger(t) |\emptyset \rangle$ の形をしています。ここで、$i$ は波導のインデックスです。どのように一光子波束を作成するかについては [`onephoton`](@ref) を、複数のシステムがある場合のインデックスの付け方については [`view_waveguide`](@ref) を参照してください。

# 例

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

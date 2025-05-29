二光子波束を次の形で作成します：$\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$ ここで、$i$ と $j$ は波導のインデックスです。これを `Ket` として返します。

[`WaveguideBasis`](@ref) および [`TwoPhotonView`](@ref) を参照して、状態の表示方法を確認してください。

#例 1つの波導のみを使用して二光子状態を作成する（関数を使用）：

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

1つの波導のみを使用して二光子状態を作成する（行列を使用）：

```@example twophotview
ψ = twophoton(bw,ones((length(times),length(times))),norm=false);
ψview = TwoPhotonView(ψ);
ψview == ones((length(times),length(times)))
```

複数の波導を使用して波導2で二光子状態を作成する：

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,2,(t1,t2)->1,norm=false);
```

波導1と2を横断する二光子状態を作成する：

```@example twophotview
bw = WaveguideBasis(2,3,times)
ψ = twophoton(bw,1,2,(t1,t2)->1,norm=false);
```

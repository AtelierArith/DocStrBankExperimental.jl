波導内の形状 $W^\dagger(\xi) |0 \rangle = \int_{t_0}^{t_{end}} dt  \xi(t) w_{\mathrm{i}}^\dagger(t) |\emptyset \rangle = \sum_{k}$ の一光子波束を作成し、それを `Ket` として返します。状態の表示方法については、[`WaveguideBasis`](@ref) と [`OnePhotonView`](@ref) を参照してください。

# 例

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

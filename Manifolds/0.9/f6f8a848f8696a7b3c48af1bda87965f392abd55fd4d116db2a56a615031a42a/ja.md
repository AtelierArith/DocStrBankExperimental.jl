```
 project(G::UnitaryMatrices, p)
 project(G::OrthogonalMatrices, p)
```

点 $p ∈ 𝔽^{n×n}$ をフロベニウスノルムの下で $\mathrm{U}(n,𝔽)=$[`Unitary(n,𝔽)`](@ref) の最近接点に射影します。もし $p = U S V^\mathrm{H}$ が $p$ の特異値分解であるなら、射影は次のようになります。

$$
  \operatorname{proj}_{\mathrm{U}(n,𝔽)} \colon p ↦ U V^\mathrm{H}.
$$

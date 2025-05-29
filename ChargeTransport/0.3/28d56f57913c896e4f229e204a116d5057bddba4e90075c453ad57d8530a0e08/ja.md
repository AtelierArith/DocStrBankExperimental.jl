```julia
breaction!(
    f,
    u,
    bnode,
    data,
    _::Type{ChargeTransport.SchottkyBarrierLowering}
) -> Any

```

シュottky境界条件を追加の低下とともに作成します。これは次のようにモデル化されます。

$$
\psi = - \phi_S/q  + \sqrt{ -\frac{ q  \nabla_{\boldsymbol{\nu}} \psi_\mathrm{R}}{4\pi \varepsilon_\mathrm{i}}} + U
$$

、

ここで、$\psi_\mathrm{R}$は標準シュottky接点を持つ電位を示し、$\psi$と同じ空間電荷密度を持ち、$\varepsilon_\mathrm{i}}}$はイメージ力誘電率に対応します。

この追加の境界条件を解決するために、投影勾配$\nabla_{\boldsymbol{\nu}} \psi_\mathrm{R}$は境界種内に保存され、メソッドgeneric_operator!()で計算されます。

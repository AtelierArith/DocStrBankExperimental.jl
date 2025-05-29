```julia
smagorinsky_closure(
    setup
) -> IncompressibleNavierStokes.var"#closure#182"

```

Smagorinsky閉じ込めモデル`m`を作成します。モデルは`m(u, θ)`として呼び出され、Smagorinsky定数`θ`は`0`と`1`の間のスカラーである必要があります（例えば`θ = 0.1`）。

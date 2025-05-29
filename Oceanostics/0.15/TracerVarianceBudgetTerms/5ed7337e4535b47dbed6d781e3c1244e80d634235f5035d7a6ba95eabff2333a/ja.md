```julia
TracerVarianceDissipationRate(
    model,
    tracer_name;
    tracer,
    location
)

```

`tracer_name`の`model.tracers`に対する各方向の等方的な分散消散率を計算する`KernelFunctionOperation`を返します。等方的な分散消散率は次のように定義されます。

```
    χ = 2 ∂ⱼc ⋅ Fⱼ
```

ここで、`Fⱼ`は`j`方向の`c`の拡散フラックスであり、`∂ⱼ`は勾配演算子です。`χ`は上記の方程式に基づいてその保守的な定式化で実装されています。

しばしば`χ`は`χ = 2κ (∇c ⋅ ∇c)`と書かれ、これはフィッキ拡散の特別な場合です（`κ`はトレーサの拡散率です）。

ここで、適切な`tracer_index`を取得するために、`tracer`を渡す際にも`tracer_name`が必要です。`tracer`を渡す際には、この関数は次のように使用されるべきです。

```julia
grid = RectilinearGrid(size=(4, 4, 4), extent=(1, 1, 1))
model = NonhydrostaticModel(grid=grid, tracers=:b, closure=SmagorinskyLilly())

b̄ = Field(Average(model.tracers.b, dims=(1,2)))
b′ = model.tracers.b - b̄

χb = TracerVarianceDissipationRate(model, :b, tracer=b′)
```

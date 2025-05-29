```
f = transport_to(ν, μ)
```

測度 `μ` に従って分布された値 `x` を測度 `ν` に従って分布された値 `y = f(x)` に変換する [可測関数](https://en.wikipedia.org/wiki/Measurable_function) `f` を生成します。

`f` による `μ` からの [プッシュフォワード測度](https://en.wikipedia.org/wiki/Pushforward_measure) は `ν` に等しいです。

確率値の用語で言えば、これは `f(rand(μ))` が `rand(ν)` に等しいことを意味します（`rand(μ)` と `rand(ν)` がサポートされている場合）。

結果として得られる関数 `f` は、数学的に定義されている場合、`ChangesOfVariables.with_logabsdet_jacobian(f, x)` をサポートする必要があります。これにより、測度 `μ` の密度から測度 `ν` の密度を `f` を介して導出できます（適切な基準測度を使用して）。

`μ` から `ν` への変換が見つからない場合は、`NoTransportOrigin{typeof(ν),typeof(μ)}` を返します。

測度タイプ `MyMeasure` の変換ルールを追加するには、次のように特化します。

  * `MeasureBase.transport_def(ν::SomeStdMeasure, μ::CustomMeasure, x) = ...`
  * `MeasureBase.transport_def(ν::MyMeasure, μ::SomeStdMeasure, x) = ...`

および/または

  * `MeasureBase.transport_origin(ν::MyMeasure) = SomeMeasure(...)`
  * `MeasureBase.from_origin(μ::MyMeasure, x) = y`
  * `MeasureBase.to_origin(μ::MyMeasure, y) = x`

そして、`MeasureBase.getdof(μ::MyMeasure)` が正しく定義されていることを確認します。

`StdUniform`、`StdExponential`、または `StdLogistic` のような標準測度タイプも、変換のソースまたはターゲットとして使用できます：

```julia
f_to_uniform(StdUniform, μ)
f_to_uniform(ν, StdUniform)
```

[`getdof(μ)`](@ref)（それぞれ `ν`）に応じて、標準分布のインスタンス自体またはその累乗（例：`StdUniform()` または `StdUniform()^dof`）が変換パートナーとして選択されます。

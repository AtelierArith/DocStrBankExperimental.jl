```julia
CustomTransform(g, f, flatten; chunk, cfg)

```

カスタム変換 `y = f(transform(g, x))` をラップする型で、必要に応じて `ForwardDiff` を使用して $∂y/∂x$ の対数ヤコビアンを計算します。

通常、`g::TransformReals` ですが、整数が使用される場合は、その次元の恒等変換に相当します。

`flatten` は `f` からの結果を受け取り、冗長な要素のないフラットベクトルを返すべきです。これにより、$x ↦ y$ は全単射になります。例えば、共分散行列の場合、対角線の下の要素は削除されるべきです。

`chunk` と `cfg` は `ForwardDiff.JacobianConfig` を構成するために使用できます。`cfg` は直接使用され、`chunk = ForwardDiff.Chunk{N}()` を使用して型安定な構成を取得できます。

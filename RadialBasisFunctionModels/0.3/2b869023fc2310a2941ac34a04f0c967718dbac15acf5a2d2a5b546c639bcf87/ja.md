```
RBFModel( features, labels, φ = Multiquadric(), poly_deg = 1; kwargs ... )
```

`features` にある特徴ベクトルと対応する `labels` にあるラベルから `RBFModel` を構築します。ここで、`φ` は `RadialFunction` または `RadialFunction` のベクトルです。

スカラー データを使用することができ、内部で変換されます。

StaticArrays を使用することができます。例えば、`features :: Vector{<:SVector}` のように。`SVector` のみを提供することで、構築が速くなる可能性があります。

多項式テールの次数 `poly_deg` が小さすぎる場合、`cpd_order(φ)-1` に設定されます。

RBF センターが `features` と等しくない場合、キーワード引数 `centers` を使用してセンターのリストを渡すことができます。`φ` がベクトルの場合、`centers` と `φ` の長さは等しくなければならず、`centers[i]` は `φ[i]` と組み合わせて `ShiftedKernel` を構築するために使用されます。

`features` に 1D データがある場合、モデルの出力は 1D ベクトルになります。スカラーであるべき場合は、キーワード引数 `vector_output` を `false` に設定してください。

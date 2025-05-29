```
collocation_points(
    B::AbstractBSplineBasis,
    method::SelectionMethod = default_method(B),
)
```

スプラインの評価のために適応されたコレクションポイントを定義して返します。

返されるコレクションポイントの数は、基底の関数の数と等しくなります。

`B` が境界値問題に適応された [`RecombinedBSplineBasis`](@ref) の場合、コレクションポイントは境界に含まれません。これは、境界条件が基底によって暗黙的に満たされるためです。

原則として、コレクションポイントの選択は一意ではありません。選択方法は `method` 引数を介して選択できます。現在、以下の方法が受け入れられています：

  * [`Collocation.AvgKnots()`](@ref);
  * [`Collocation.SameAsKnots()`](@ref)、これは基底の長さがノットの数と等しいことを要求します。

前者がデフォルトですが、*偶数*次数 $k$ の周期Bスプライン基底（[`PeriodicBSplineBasis`](@ref)）の場合、`SameAsKnots` がデフォルトです。（奇数次数のBスプラインの場合、これは非可逆なコレクション行列を引き起こす可能性があります。）

また、[`collocation_points!`](@ref)も参照してください。

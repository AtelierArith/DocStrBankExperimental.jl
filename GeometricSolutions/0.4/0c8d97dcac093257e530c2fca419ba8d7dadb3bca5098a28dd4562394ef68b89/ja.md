`GeometricSolution`: 幾何微分方程の解

GeometricProblemの解を保存するために必要なすべてのフィールドを含みます。

### フィールド

  * `t`:  時間ステップ
  * `s`:  各解成分のためのDataSeriesのNamedTuple
  * `step`: 毎ステップ't'の時間ステップを保存 (デフォルト: 1)
  * `nstore`: 保存する時間ステップの数
  * `offset`: 現在の時間ステップのオフセット

### コンストラクタ

```julia
GeometricSolution(problem, step = 1)
```

`Solution`を初期化する通常の方法は、[`GeometricProblem`](@ref)を渡すことです。これは例えば、[`ODEProblem`](@ref)や[`PODEProblem`](@ref)である可能性があります。オプションのパラメータ`step`は、解を保存するための間隔を決定します。すなわち、`step > 1`の場合、実際に保存されるのは毎`step`'th'の解のみです。

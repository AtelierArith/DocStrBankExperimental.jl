```
GetModel(func::AbstractODEFunction{T}, SplitterFunction::Function, PreObservationFunction::Function; tol::Real=1e-7, meth::AbstractODEAlgorithm=Tsit5(), Domain::Union{HyperCube,Nothing}=nothing, inplace::Bool=true)
```

与えられたODEシステムを進化させ、その後`ObservationFunction`を適用して予測を生成する`ModelMap`を返します。ここで、ODEの初期条件は`SplitterFunction`を使用してパラメータ`θ`から生成され、例えばデータから推定することができます。

`SplitterFunction`は`F(θ) -> (u0, p)`の形式である必要があります。つまり、出力は`Tuple`であり、最初のエントリはODEモデルの初期条件であり、2番目のエントリは`ODEFunction`に入るパラメータを構成します。通常、`SplitterFunction`が初期条件`u0`を`MVector`または`MArray`型で出力することを確認することで、かなりの追加パフォーマンスを得ることができます。これは、コンポーネントが約100未満の場合です。

`ObservationFunction`は`F(u) -> Vector`または`F(u,t) -> Vector`または`F(u,t,θ) -> Vector`の形式である必要があります。内部的に、`ObservationFunction`は自動的に`F(u,t,θ)`としてラップされます。これは、すでに3つの引数を受け入れるように定義されていない場合です。

!!! note
    `ObservationFunction`に渡されるベクトル`θ`は、`SplitterFunction`に渡されるのと同じ`θ`です。つまり、分割前のものです。これは、一般的に`ObservationFunction`も初期条件に依存する可能性があるためです。


`Domain`を提供することで、モデルのパラメータを特定の範囲に制約することができ、フィッティングプロセスに役立ちます。

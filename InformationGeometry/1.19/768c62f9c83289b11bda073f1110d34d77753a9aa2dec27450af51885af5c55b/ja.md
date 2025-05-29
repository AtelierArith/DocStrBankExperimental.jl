```
GetModel(func::ODEFunction, SplitterFunction::Function, observables::Union{AbstractVector{<:Int},BoolArray}; tol::Real=1e-7, meth::AbstractODEAlgorithm=Tsit5(), Domain::Union{HyperCube,Nothing}=nothing, inplace::Bool=true)
```

与えられたODEシステムを進化させ、`u[observables]`を返して予測を生成する`ModelMap`を返します。ここで、ODEの初期条件は、データから推定することを可能にする`SplitterFunction`を使用してパラメータ`θ`から生成されます。

`SplitterFunction`は`F(θ) -> (u0, p)`の形式である必要があります。つまり、出力は`Tuple`であり、最初のエントリはODEモデルの初期条件であり、2番目のエントリは`ODEFunction`に入るパラメータを構成します。通常、`SplitterFunction`が初期条件`u0`を`MVector`または`MArray`型で出力することを保証することで、かなりのパフォーマンス向上が得られます。コンポーネントが約100未満の場合です。

`Domain`を提供することで、モデルのパラメータを特定の範囲に制約することができ、フィッティングプロセスに役立ちます。

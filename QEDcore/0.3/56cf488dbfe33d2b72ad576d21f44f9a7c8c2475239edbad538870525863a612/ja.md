```
AbstractTwoBodyRestSystem <: AbstractTwoBodyInPhaseSpaceLayout
```

一つの粒子が系のフレーム内で静止している二体システムの位相空間レイアウトを表す抽象型です。

`AbstractTwoBodyRestSystem`の具体的なサブタイプは、通常、静止していない粒子の運動量をパラメータ化するために使用される座標系を指定します。例えば、[`Energy`](@ref)、[`SpatialMagnitude`](@ref)、[`CenterOfMomentumEnergy`](@ref)、または[`Rapidity`](@ref)などです。座標系の選択は、入射粒子の運動量の構築方法に影響を与えます。

この型は、二体散乱または崩壊過程のための静止系の仮定に依存するカスタムレイアウトを定義するための基盤として機能し、[`QEDbase._build_momenta`](@extref)のような運動量構築関数におけるメソッドディスパッチを容易にします。

# 関連項目

  * [`TwoBodyRestSystem`](@ref): 静止していない粒子を記述するためのさまざまな一変数座標をサポートする`AbstractTwoBodyRestSystem`の具体的な実装です。

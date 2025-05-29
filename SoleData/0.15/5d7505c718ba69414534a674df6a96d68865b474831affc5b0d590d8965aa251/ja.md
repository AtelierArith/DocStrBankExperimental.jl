```
representatives(
    fr::AbstractFrame{W},
    S::W,
    ::AbstractRelation,
    ::AbstractCondition
) where {W<:AbstractWorld}
```

存在モーダル接続詞を通じて真理値を計算し伝播させるために必要な（少数の）*代表的な*アクセス可能な世界へのイテレータを返します。この最適化が可能な場合（例えば、スカラー条件に対して特定の式をチェックする際）、それは「ワンステップ」最適化をさらに強化することを可能にします（[`AbstractOneStepMemoset`](@ref)を参照）。

例えば、長さ100の1次元`FullDimensionalFrame`を持つクリプケ構造を考え、[`SoleLogics.Interval`](@ref) `SoleLogics.Interval{Int64}(1, 2)`に対して「⟨L⟩(max[V1] ≥ 10)」という式をチェックする問題を考えます（ここで`L`はアレンの「後」関係であり、[`SoleLogics.IA_L`](@ref）を参照）。すべての世界で計算された（最大の）「max[V1]」と10を比較することは、式をチェックするためのナイーブな戦略です。しかし、この場合、単一の`Interval` SoleLogics.Interval{Int64}(2, 101)で計算された「max[V1]」と10を比較するだけで、構造が式を満たすかどうかを確立するのに十分です。関係、特徴、テスト演算子（または、より良く言えばその*集約器*）に応じて、同様のケースが発生します。

このメソッドは`accessibles`にフォールバックすることに注意してください。

[`SoleLogics.accessibles`](@ref)、[`ScalarCondition`](@ref)、[`SoleLogics.AbstractFrame`](@ref)も参照してください。

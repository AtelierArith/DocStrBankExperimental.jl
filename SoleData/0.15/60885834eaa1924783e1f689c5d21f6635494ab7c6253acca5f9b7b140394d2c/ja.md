```
struct ScalarMetaCondition{FT<:AbstractFeature,O<:TestOperator} <: AbstractCondition{FT}
    feature::FT
    test_operator::O
end
```

スカラー比較メソッドを表すメタ条件です。ここで、`feature`は論理データセットのインスタンスの世界で計算できるスカラー関数です。テスト演算子は、計算された特徴値と外部の閾値（`ScalarCondition`を参照）を比較する二項数学的関係です。メタ条件は、自由な閾値に伴って生じる無限の条件の集合を表すためにも使用できます（`UnboundedScalarAlphabet`を参照）： ${min[V1] ≥ a, a ∈ ℝ}$。

さらに[`AbstractCondition`](@ref)、[`ScalarCondition`](@ref)を参照してください。

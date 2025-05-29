```
RecordChange <: RecordAction
```

イテレートの変化量をデバッグします（最後のイテレーション中の[`AbstractManoptSolverState`](@ref)`(s)`の[`get_iterate`](@ref)を参照）。

# フィールド

  * `storage`                   : 最後のイテレートを保存するための[`StoreStateAction`](@ref)（少なくとも）を使用して、これを最後の値として使用し（変化を計算するため）、ソルバーの他のコンポーネントと共有される潜在的なキャッシュとして機能します。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆再traction $\operatorname{retr}^{-1}$、再tractionとその逆に関するセクションを参照してください[@extref ManifoldsBase :doc:`retractions`]。
  * `recorded_values`           : 記録された値を保存するためのもの

# コンストラクタ

```
RecordChange(M=DefaultManifold();
    inverse_retraction_method = default_inverse_retraction_method(M),
    storage                   = StoreStateAction(M; store_points=Tuple{:Iterate})
)
```

前述のフィールドをキーワードとして使用します。`DefaultManifold`の場合、ストレージフィールドのみが使用されます。実際の多様体を提供すると、デフォルトのストレージが効率的なポイントストレージに移動します。

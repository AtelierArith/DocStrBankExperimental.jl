```
simulation(filter::AbstractFilter, b0::GaussianBelief,
            action_sequence::Vector{AbstractVector}})
```

シミュレーションを実行して位置と測定値を取得します。サンプルの開始点はGaussianBelief b0から取得され、action_sequenceはAbstractFilter filterによって指定された加法的ガウスノイズで実行され、シミュレーションされた状態と測定履歴を返します。

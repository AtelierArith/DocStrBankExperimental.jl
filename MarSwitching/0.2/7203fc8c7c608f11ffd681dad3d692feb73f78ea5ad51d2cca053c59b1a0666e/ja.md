```
expected_duration(model::MSM, exog_tvtp::VecOrMat{AbstractFloat})
```

非TVTPモデルの場合、各状態の期待される持続時間のベクトルを返します。TVTPモデルの場合、時刻tにおける各状態の期待される持続時間の行列を返します。    

式: `1 / (1 - P[i,i])` またはTVTPの場合 - `1 / (1 - P[i,i, t])`

# 引数

  * `model::MSM`: 推定されたモデル。
  * `exog_tvtp::VecOrMat{AbstractFloat}`: tのTVTPモデル用のオプションの外生変数。提供されない場合、インサンプルデータが使用されます。

詳細は [`ergodic_probs`](@ref) を参照してください。

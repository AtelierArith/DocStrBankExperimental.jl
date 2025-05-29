```
ergodic_probs(model::MSM, exog_tvtp::VecOrMat{V})
```

非TVTPモデルに適用すると、各状態のエルゴード確率の`k`サイズのベクターを返します。TVTPモデルの場合、時間tにおける各状態のエルゴード確率の$T \times K$の行列を返します。

# 引数

  * `model::MSM`: 推定されたモデル。
  * `exog_tvtp::VecOrMat{AbstractFloat}`: tにおけるTVTPモデルのためのオプションの外生変数。提供されない場合は、インサンプルデータが使用されます。

他にも[`expected_duration`](@ref)を参照してください。

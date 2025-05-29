```
get_state(ctmc::CTMC, t::AbstractFloat)
```

CTMCの特定の時点での状態を取得します。

# 引数

  * `ctmc::CTMC`: クエリするCTMC
  * `t::AbstractFloat`: 興味のある時点

# 戻り値

  * `Int`: 時間tにおけるチェーンの状態

# 注意

遷移時間を検索して、時間tにアクティブな状態を見つけます。時間tの直前の最後の遷移で入った状態を返します。

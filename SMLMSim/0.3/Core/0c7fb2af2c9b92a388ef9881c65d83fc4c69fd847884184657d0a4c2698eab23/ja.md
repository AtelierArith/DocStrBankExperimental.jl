```
get_next(ctmc::CTMC, t::AbstractFloat)
```

特定の時点の後の次の状態遷移を取得します。

# 引数

  * `ctmc::CTMC`: クエリするCTMC
  * `t::AbstractFloat`: 現在の時点

# 戻り値

  * `Tuple{Int,AbstractFloat}`: (次の*状態, 遷移*時間)

# 注意

現在の時点から前方に検索し、次に入る状態とその時点を返します。

```
merge_close_lines(linelist; merge_distance=0.2)
```

`linelist`内の線の種と波長のリストを生成し、`merge_distance`（デフォルト: 0.2 Å）内にある同じ種の線をマージします。これは、[`prune_linelist`](@ref)を実行した後にプロット内の線にラベルを付けるのに便利です。

# 引数

  * `linelist`: linelist（`Line`オブジェクトのベクター）

# キーワード引数

  * `merge_distance=0.2`: 同じ種の線を1つのエントリにマージするための最大距離（Å）

# 戻り値

マージされた線の各セットのgf加重波長（Å）を持つタプル`(wl, wl_low, wl_high, species)`のベクターを返します。`wl_low`と`wl_high`はそれぞれの最高波長と最低波長であり、`species`は線の種を識別する文字列（`Korg.Species`ではない）です。これらは波長順に並べられます。

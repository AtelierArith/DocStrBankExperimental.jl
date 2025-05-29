```
root_locus(g_ol, max_mag_Kc=10.0, nb_pts=500, savename=nothing, legend_pos=:rt)
```

オープンループ伝達関数 `g_ol` のルートロケーションプロットを視覚化します。

# 引数

  * `g_ol::TransferFunction`: 閉ループシステムのオープンループ伝達関数
  * `max_mag_Kc::Float64=10.0`: ルートが平面を横断するのを見るために `g_ol` のゲインをスケーリングする最大の大きさ
  * `nb_pts::Int=500`: 探索するゲインの数。解像度を高くするために増やします。
  * `legend_pos::Symbol`: 凡例を配置するためのMakieコマンド

# 戻り値

さらなる修正のための `CairoMakie.jl` `Figure` オブジェクト。

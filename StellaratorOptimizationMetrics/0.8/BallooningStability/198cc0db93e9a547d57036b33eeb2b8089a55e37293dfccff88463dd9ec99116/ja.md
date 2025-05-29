```
cobra_opt(eq, slist, nwells; θs, ζs, mode, geom_input, tokamak_input,
               lscreen, print_progress, interp, reltol, return_all, return_locs)
```

最大不安定固有値の位置を計算します

# 引数

  * `eq::E`: Vmec または DESC 平衡
  * `slist::AbstractVector`: s 値のリスト
  * `nwells::Integer`: 含めるヘリカルウェルの数

# オプション入力

  * `θs::AbstractVector`: 開始 θ 値のベクトル（ラジアン単位）
  * `ζs::AbstractVector`: 開始 ζ 値のベクトル（フィールド周期に正規化されたラジアン単位）
  * `reltol::Number`: 係数補間のための相対許容誤差入力
  * `np::Integer`: 固有値計算に使用されるポイントの数
  * `print_progress::Bool`: 新しい s-サーフェスが使用されるたびに印刷する（興奮を加える）
  * `spline::Bool`: スプラインを使用して補間する
  * 

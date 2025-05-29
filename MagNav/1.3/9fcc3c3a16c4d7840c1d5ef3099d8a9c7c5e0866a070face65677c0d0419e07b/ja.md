```
gif_animation_m3(TL_perm::AbstractMatrix, TL_induced::AbstractMatrix, TL_eddy::AbstractMatrix,
                 TL_aircraft::AbstractMatrix, B_unit::AbstractMatrix, y_nn::AbstractMatrix,
                 y::Vector, y_hat::Vector, xyz::XYZ,
                 filt_lat::Vector = [],
                 filt_lon::Vector = [];
                 ind              = trues(xyz.traj.N),
                 tt_lim::Tuple    = (0, (xyz.traj(ind).N-1)*xyz.traj.dt/60),
                 skip_every::Int  = 5,
                 save_plot::Bool  = false,
                 mag_gif::String  = "comp_xai.gif")

モデル3のコンポーネントと真のスカラー磁場および予測されたスカラー磁場のGIFアニメーションを作成します。最初に`comp_m3_test()`を実行して、個々のモデルコンポーネント3を生成します。

**引数**

  * `TL_perm`:     `3` x `N`のTL永久ベクトル場の行列
  * `TL_induced`:  `3` x `N`のTL誘導ベクトル場の行列
  * `TL_eddy`:     `3` x `N`のTL渦電流ベクトル場の行列
  * `TL_aircraft`: `3` x `N`のTL航空機ベクトル場の行列
  * `B_unit`:      `3` x `N`の正規化されたベクトル磁気計測値の行列
  * `y_nn`:        `3` x `N`のベクトルニューラルネットワーク補正の行列（スカラーモデルの場合、`Bt`の方向）
  * `y`:           長さ`N`のターゲットベクトル
  * `y_hat`:       長さ`N`の予測ベクトル
  * `xyz`:         `XYZ`フライトデータ構造
  * `filt_lat`:    （オプション）長さ`N`のフィルタ出力緯度  [rad]
  * `filt_lon`:    （オプション）長さ`N`のフィルタ出力経度 [rad]
  * `ind`:         （オプション）選択されたデータインデックス
  * `tt_lim`:      （オプション）長さ`2`の開始および終了時間制限（含む） [min]
  * `skip_every`:  （オプション）フレーム間でスキップする時間ステップの数
  * `save_plot`:   （オプション）trueの場合、`g1`を`mag_gif`として保存
  * `mag_gif`:     （オプション）保存する磁場GIFファイルのパス/名前（`.gif`拡張子はオプション）

**戻り値**

  * `g1`: 磁場GIFアニメーション

**例**

```

julia gif*animation*m3(TL*perm, TL*induced, TL*eddy, TL*aircraft, B*unit,                  y*nn, y, y*hat, xyz, filt*lat, filt*lon; ind=ind, tt*lim=(0.0,10.0),                  skip*every=5, save*plot=false, mag*gif="comp*xai.gif") ```

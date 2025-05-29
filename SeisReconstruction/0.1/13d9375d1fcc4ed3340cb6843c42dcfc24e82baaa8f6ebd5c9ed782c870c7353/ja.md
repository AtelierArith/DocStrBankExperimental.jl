SeisSpitzFX(d;<keyword arguments>)

第一階f-x補間をSpitzの方法を使用して行います。入力サイズはsize(d)= (nt,nh)です。出力サイズは(nt,2*nh-1)です。

# 引数

-`dt`: サンプリング間隔（秒） -`npf`: 予測フィルタの長さ

  * `pre1` : Pef推定のための前処理の割合
  * `pre2` : 欠損サンプルの推定のための前処理の割合
  * `flow` : 再構成する最小時間周波数（Hz）
  * `fhigh` : 再構成する最大時間周波数（Hz）

# 例

'''julia d_interp = SeisSpitzFX(d) '''

  * 参考文献: Spitz, S., 1991, Seismic trace interpolation in the F-X domain: Geophysics, 56, 785-794.

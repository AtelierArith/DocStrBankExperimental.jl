`SuperlinearDimer`: KastnerのJCP 128, 014106 (2008) 記事およびASE実装に基づくダイマーのバリアント

### パラメータ

  * maximum_translation : ステップサイズを制御する（実際の値、パラメータではない）
  * max*num*rot : 各ステップでの最大回転数
  * trial_angle : 回転後のエネルギー変化を予測するための角度増分
  * trial*trans*step : 翻訳後のエネルギー変化を予測するためのステップ増分
  * use*central*forces : ???
  * extrapolate : Kastner外挿を行うかどうか
  * translation_method : "CG" のみが実装されている

### 共有パラメータ

  * `tol_trans` : 翻訳残差許容値
  * `tol_rot` : 回転残差許容値
  * `maxnumdE` : 最大dE評価数
  * `len` : ダイマーの長さ（すなわち、2つのウォーカの距離）
  * `precon` : 前処理器
  * `precon_prep!` : 前処理器の更新関数
  * `verbose` : どれだけの情報を印刷するか（0: なし、1: イテレーションの終わり、2: 各イテレーション、3: ファイルログ）
  * `precon_rot` : 回転ステップを前処理するかどうか（真/偽）
  * `rescale_v` : 各ステップ後に `v` を単位長に再スケールするべきか

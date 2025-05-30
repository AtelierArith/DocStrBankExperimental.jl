`BBDimer`: Barzilai-Borwein ステップサイズを用いたダイマー法 + Armijo タイプの安定性チェック。

### パラメータ:

  * `a0_trans` : 初期平行移動ステップ
  * `a0_rot` : 初期回転ステップ
  * `ls` : ラインサーチ

### 共有パラメータ

  * `tol_trans` : 平行移動残差許容値
  * `tol_rot` : 回転残差許容値
  * `maxnumdE` : dE 評価の最大数
  * `len` : ダイマーの長さ（すなわち、2つのウォーカーの距離）
  * `precon` : 前処理器
  * `precon_prep!` : 前処理器の更新関数
  * `verbose` : どれだけの情報を出力するか（0: なし、1: イテレーションの終わり、2: 各イテレーション、3: ファイルログ）
  * `precon_rot` : 回転ステップを前処理するかどうかの真偽値
  * `rescale_v` : 各ステップ後に `v` を単位長さに再スケールするべきか

## 参考文献

この手法は以下のアイデアを組み合わせています。

[ZDZ] 最適化に基づく縮小ダイマー法による遷移状態の発見 SIAM J. Sci. Comput., 38(1), A528–A544 Lei Zhang, Qiang Du, and Zhenzhen Zheng DOI:10.1137/140972676

および

[GOP] 前処理とラインサーチを用いたダイマー型鞍点探索アルゴリズム Math. Comp. 85, 2016 N. Gould and C. Ortner and D. Packwood http://arxiv.org/abs/1407.2817

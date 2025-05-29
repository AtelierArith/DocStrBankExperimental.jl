`ODEString`: NEB法による適応ODEステップサイズ選択。

### パラメータ:

  * `reltol` : ODEソルバーの相対許容誤差
  * `threshold` : 誤差推定のための閾値
  * `a0` : 初期ステップ。a0が渡されない場合はデフォルトを使用

### NEB専用パラメータ:

  * `k` : バネ定数
  * `interp` : 補間の次数 (1: 中央差分, >1: 次数interpのスプライン)

### 共有パラメータ

  * `tol` : 残差許容誤差
  * `maxnit` : 最大反復回数
  * `precon_scheme` : 前処理器スキーム (localPrecon(), globalPrecon())
  * `path_traverse` : エネルギーを計算するための経路のトラバース方法 (serial(), palindrome())
  * `fixed_ends` : 経路の端を固定するかどうかの真偽値、デフォルトはfalse
  * `verbose` : 出力する情報の量 (0: なし, 1: 反復の終わり, 2: 各反復, 3: ファイルログ)

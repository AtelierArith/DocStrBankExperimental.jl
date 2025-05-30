`ODEString`: 適応的ODEステップサイズ選択を持つ文字列メソッド。

### パラメータ:

  * `reltol` : ODEソルバーの相対許容誤差
  * `threshold` : 誤差推定のための閾値
  * `a0` : 初期ステップ。a0が渡されない場合はデフォルトを使用

### 共有パラメータ

  * `tol` : 残差許容誤差
  * `maxnit` : 最大反復回数
  * `precon_scheme` : 前処理器スキーム (localPrecon(), globalPrecon())
  * `path_traverse` : エネルギーを計算するためのパスの横断方法 (serial(), palindrome())
  * `fixed_ends` : パスの端を固定するかどうかの真偽値、デフォルトはfalse
  * `verbose` : どれだけの情報を印刷するか (0: なし, 1: 反復の終わり, 2: 各反復, 3: ファイルログ)

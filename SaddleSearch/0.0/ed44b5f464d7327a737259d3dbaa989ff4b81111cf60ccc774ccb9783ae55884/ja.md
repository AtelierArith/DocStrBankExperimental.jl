`AccelString`: モーメント降下法を使用してエネルギー最小化を加速する文字列メソッド。

### パラメータ:

  * `a0` : 初期ステップ。a0が渡されない場合はデフォルトを使用
  * `b` : モーメント項の減衰係数
  * `finite_diff_scheme` : ダンプ波動方程式の離散化の選択

### 共有パラメータ

  * `tol` : 残差許容値
  * `maxnit` : 最大反復回数
  * `precon_scheme` : 前処理器スキーム (localPrecon(), globalPrecon())
  * `path_traverse` : エネルギーを計算するためのパスの横断方法 (serial(), palindrome())
  * `fixed_ends` : パスの端を固定するかどうかの真偽値、デフォルトはfalse
  * `verbose` : どれだけの情報を印刷するか (0: なし, 1: 反復の終わり, 2: 各反復, 3: ファイルログ)

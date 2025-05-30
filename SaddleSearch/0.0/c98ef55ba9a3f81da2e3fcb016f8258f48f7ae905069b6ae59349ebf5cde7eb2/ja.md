`StaticNEB`: 最も基本的なNEBバリアントで、固定ステップサイズでポテンシャル勾配フローを統合します。

### パラメータ:

  * `alpha` : オイラー法の統合ステップ長

### NEB専用パラメータ:

  * `k` : バネ定数
  * `interp` : 補間の次数 (1: 中央差分, >1: 次数interpのスプライン)

### 共有パラメータ

  * `tol` : 残差許容値
  * `maxnit` : 最大反復回数
  * `precon_scheme` : 前処理器スキーム (localPrecon(), globalPrecon())
  * `path_traverse` : エネルギーを計算するためのパスの横断方法 (serial(), palindrome())
  * `fixed_ends` : パスの端を固定するかどうかの真偽値、デフォルトはfalse
  * `verbose` : 出力する情報の量 (0: なし, 1: 反復の終わり, 2: 各反復, 3: ファイルログ)

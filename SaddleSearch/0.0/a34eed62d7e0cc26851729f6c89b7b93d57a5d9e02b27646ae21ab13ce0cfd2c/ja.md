`StaticString`: 最も基本的な文字列のバリアントで、固定ステップサイズでの潜在的な勾配フローを統合しています。

### パラメータ:

  * `alpha` : オイラー法の統合ステップ長

### 共有パラメータ

  * `tol` : 残差許容値
  * `maxnit` : 最大反復回数
  * `precon_scheme` : 前処理器スキーム (localPrecon(), globalPrecon())
  * `path_traverse` : エネルギーを計算するためのパスのトラバース方法 (serial(), palindrome())
  * `fixed_ends` : パスの端を固定するかどうかの真偽値、デフォルトはfalse
  * `verbose` : 出力する情報の量 (0: なし, 1: 反復の終わり, 2: 各反復, 3: ファイルログ)

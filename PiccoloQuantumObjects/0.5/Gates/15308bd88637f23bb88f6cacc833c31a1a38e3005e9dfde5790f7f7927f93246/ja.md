定数辞書 `GATES` は、共通の量子ゲート行列を複素数値行列として含んでいます。各ゲートはそのユニタリ行列で表されます。

  * `GATES[:I]` - 単位行列: 状態を変更しません。
  * `GATES[:X]` - パウリ-X (NOT): キュービットの状態を反転させます。
  * `GATES[:Y]` - パウリ-Y: ブロッホ球のY軸周りにキュービットの状態を回転させます。
  * `GATES[:Z]` - パウリ-Z: キュービットの状態の位相を反転させます。
  * `GATES[:H]` - ハダマード: 基底状態を変換することで重ね合わせを作成します。
  * `GATES[:CX]` - 制御-X (CNOT): 最初のキュービット (制御) が |1⟩ の場合、2番目のキュービット (ターゲット) を反転させます。
  * `GATES[:CZ]` - 制御-Z (CZ): 最初のキュービット (制御) が |1⟩ の場合、2番目のキュービット (ターゲット) の位相を反転させます。
  * `GATES[:XI]` - 複素: 複素演算のためのゲートです。
  * `GATES[:sqrtiSWAP]` - iSWAPの平方根: 位相を伴って2つのキュービットを部分的にスワップします。

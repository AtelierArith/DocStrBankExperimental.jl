投影ベースの微分理想の表現を格納するための構造（セクション2.3を参照 https://arxiv.org/abs/2111.00991）。以下のフィールドを含みます：

  * `y_names` - プロファイル内の有限次数の変数の名前（通常は出力）
  * `u_names` - プロファイル内の無限次数の変数の名前（通常は入力）
  * `param_names` - パラメータの名前
  * `profile` - 有限次数の `y_names` から次数への辞書としてのPB-表現のプロファイル（定義2.13を参照）
  * `projections` - `y_names` から投影への辞書としての対応する投影（定義2.15を参照）

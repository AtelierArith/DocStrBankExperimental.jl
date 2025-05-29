シミュレーションパラメータ。

  * `iters::Int64`: USの反復回数
  * `steps::Int64`: 実行または単一反復のためのMCステップ
  * `max_bias_diff::Float64`: バイアスエネルギーの最大変化 (kbT)
  * `write_interval::Int64`: 出力ファイルへの書き込み間のステップ数
  * `radius_move_freq::Float64`: 半径移動の頻度（残りはフィラメントの移動）
  * `filebase::String`: 出力ファイルベース（ファイルパスを含む）
  * `analytical_biases::Bool`: 開始バイアスを生成するために解析モデルを使用する
  * `read_biases::Bool`: ファイルから開始バイアスを読み込む
  * `biases_filename::String`: バイアスを読み込むファイル
  * `restart_iter::Int64`: 開始する反復
  * `binwidth::Int64`: 格子高さバイアスのビンの幅（ビンなしの場合は1に設定）

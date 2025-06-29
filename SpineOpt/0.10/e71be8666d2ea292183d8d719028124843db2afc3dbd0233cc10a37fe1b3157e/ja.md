```
solve_model!(m; <キーワード引数>)
```

指定されたSpineOptモデルを解決し、出力を保存します。

# 引数

  * `log_level::Int=3`: ログレベルを制御する整数。
  * `update_names::Bool=false`: モデルがロールした後に変数と制約の名前を更新するかどうか（高コスト）。
  * `write_as_roll::Int=0`: 0より大きく、かつ実行がローリングホライズンを持つ場合、その数だけウィンドウごとに結果を書き込む。
  * `resume_file_path::String=nothing`: `write_as_roll`が1以上のローリングホライズン最適化にのみ関連。指定されたパスのファイルに前回の実行からの再開データが含まれている場合、そのポイントから実行を開始します。また、モデルがロールし、結果が出力データベースに書き込まれる際に、その同じファイルに再開データを保存します。
  * `calculate_duals::Bool=false`: モデル解決後に双対を計算するかどうか。
  * `output_suffix::NamedTuple=(;)`: 出力に追加するためのもの。
  * `log_prefix::String`="": ログメッセージの前に追加する文字列。

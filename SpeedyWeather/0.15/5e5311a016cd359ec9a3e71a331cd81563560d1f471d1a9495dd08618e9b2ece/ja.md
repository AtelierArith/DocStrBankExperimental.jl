JLD2ファイルにPrognosticVariablesおよびDiagnosticVariables構造体を直接保存するための出力ライター。これらの出力には、すべての内部スケーリングと単位が適用されています。フィールドは次のとおりです。

  * `active::Bool`
  * `path::String`: [OPTION] 出力フォルダーへのパス、run_????がその中に作成されます
  * `id::String`: [OPTION] 実行識別番号/文字列
  * `run_path::String`
  * `filename::String`: [OPTION] 出力jld2ファイルの名前
  * `write_restart::Bool`: [OPTION] output==trueの場合、再起動ファイルも書き込みますか？
  * `pkg_version::VersionNumber`
  * `output_dt::Dates.Second`: [OPTION] 出力頻度、タイムステップ
  * `merge_output::Bool`: [OPTION] ファイルを再オープンして、すべてを1つの大きなベクターにマージするために再保存します。ファイルがメモリに対して大きすぎる場合はオフにしてください。
  * `output_prognostic::Bool`: [OPTION] PrognosticVariablesを出力します
  * `output_diagnostic::Bool`: [OPTION] DiagnosticVariablesも出力します
  * `output_every_n_steps::Int64`
  * `timestep_counter::Int64`
  * `output_counter::Int64`
  * `jld2_file::Union{Nothing, JLD2.JLDFile}`

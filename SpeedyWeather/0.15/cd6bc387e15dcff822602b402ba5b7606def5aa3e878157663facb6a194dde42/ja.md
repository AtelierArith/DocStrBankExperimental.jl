フィードバック構造体は、進行状況メーターのようなコマンドラインフィードバックのオプションとオブジェクトを含みます。

  * `verbose::Bool`: REPLにフィードバックを印刷しますか？デフォルトはisinteractive()で、インタラクティブREPLモードではtrueです
  * `debug::Bool`: 予測変数にNaRがあるかどうかをチェックします
  * `output::Bool`: progress.txtファイルを書き込みますか？状態はNetCDFOutput.outputと同期しています
  * `id::String`: 実行の識別、::OutputWriterから取得
  * `run_path::String`: 実行フォルダへのパス、::OutputWriterから取得
  * `progress_meter::ProgressMeter.Progress`: 進行状況に関連するすべてを含む構造体
  * `progress_txt::IOStream`: 出力がない場合、txtはNothingです
  * `nars_detected::Bool`: シミュレーションでInfs/NaNsが発生しましたか？

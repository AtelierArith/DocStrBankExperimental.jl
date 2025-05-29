```
pprof([data, [lidict]];
        web = true, webhost = "localhost", webport = 57599,
        out = "profile.pb.gz", from_c = true, full_signatures = true, drop_frames = "",
        keep_frames = "", ui_relative_percentages = true, sampling_delay = nothing,
     )
pprof(FlameGraphs.flamegraph(); kwargs...)
```

収集された `Profile` データを取得し、`pprof` 形式にエクスポートし、（オプションで）結果をインタラクティブに表示するための `pprof` ウェブサーバーを開きます。

`web=true` の場合、ウェブサーバーはバックグラウンドで開かれます。 `pprof()` を再実行すると、新しい出力を使用するためにウェブサーバーが更新されます。

出力ファイルを手動で編集した場合、`PProf.refresh()` は出力ファイルを上書きすることなくサーバーを更新します。 `PProf.kill()` はサーバーを終了します。

`PProf.refresh(file="...")` を使用して、サーバーで新しいファイルを開くこともできます。

# 引数:

  * `data::Vector{UInt}`: `Profile.retrieve()` によって提供されるデータ [オプション]。
  * `lidict::Dict`: `Profile.retrieve()` によって提供されるルックアップ辞書 [オプション]。

      * プロファイリングデータをジュリアプロセス間でエクスポートするには、`Profile.retrieve()` から返される `data` と `lidict` の両方が必要です。
  * `flamegraph`: PProf は `FlameGraphs.jl` グラフオブジェクトとして渡されたプロファイルデータも受け入れます。

# キーワード引数

  * `sampling_delay::UInt64`: サンプル間の期間（ナノ秒） [オプション]。
  * `web::Bool`: 結果を表示するための `go tool pprof` インタラクティブウェブサーバーを起動するかどうか。
  * `webhost::AbstractString`: `web` を使用する場合、ウェブサーバーを起動するホスト。
  * `webport::Integer`: `web` を使用する場合、ウェブサーバーを起動するポート。
  * `out::String`: 出力用のファイル名。
  * `from_c::Bool`: `false` の場合、from_c からのフレームを除外します。デフォルトは `true`。
  * `full_signatures::Bool`: `true` の場合、メソッドは引数の型を含む署名として印刷されます。 `false` の場合は名前のみ。例: `eval(::Module, ::Any)` 対 `eval`。
  * `drop_frames`: 関数名が正規表現文字列と完全に一致するフレームは、サンプルから削除され、その後継者も削除されます。
  * `keep_frames`: 関数名が正規表現文字列と完全に一致するフレームは、削除関数と一致しても保持されます。
  * `ui_relative_percentages`: `-relative_percentages` を pprof に渡します。ウェブ UI を通じて無視された/隠されたノードは、パーセンテージを計算する際に合計から無視されます。

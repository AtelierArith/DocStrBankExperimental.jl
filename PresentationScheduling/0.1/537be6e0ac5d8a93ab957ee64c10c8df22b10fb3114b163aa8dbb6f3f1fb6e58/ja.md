```
optimize_presentation_schedule(
    individuals :: AbstractVector{IT},
    dates :: AbstractVector{DT},
    [presentations_modify, journals_modify, cannot_attend]...; 
    kwargs...
    ) where {IT <: Union{Int, String}, DT <: Union{Date, Int}}
```

`individuals` と `dates` のイテラブルを考慮して、各発表日ごとに研究発表とジャーナルクラブ発表を個々の参加者に割り当てる会議スケジュールを計画し、各個人の発表を均等に間隔を空けて配置することを目指します。

最適化されたスケジュールを返し、JuMPモデルをラップし、テーブルとして表示します。

## オプション引数

  * `presentations_modify :: Dict{IT, Int}`: 各個人は `default_presentations` の研究発表を行う予定です（キーワード引数を参照）。これを上書きするには、個人に対して `key=>value` ペアを `presentation_modify` に追加します。例: `presentations_modify = Dict("Individual A" => 1)`。
  * `journals_modify :: Dict{IT, Int}`: `presentations_modify` と同様ですが、特定の個人のジャーナルクラブ発表の数を上書きするためのものです。
  * `cannot attend :: Dict{IT, <:AbstractVector{DT}}`: 特定の個人が発表できない日付のリストで、`dates` と重複するものです。例: `cannot_attend = Dict("Individual A" => Date("21/01/2024"))`。

オプション引数は指定されていない場合、空のコンテナがデフォルトとなります。

## キーワード引数

  * `default_presentations :: Int` (デフォルト, `2`): 各個人あたりの研究発表のデフォルト数; オプション引数 `presentations_modify` で上書き可能。
  * `default_journals :: Int` (デフォルト, `1`): 各個人あたりのジャーナルクラブ発表のデフォルト数; オプション引数 `journals_modify` で上書き可能。
  * `min_total :: Int` (デフォルト, `2`): 各会議日あたりの最小総発表数（研究 *および* ジャーナルクラブ）。
  * `max_total :: Int` (デフォルト, `4`): 各会議日あたりの最大総発表数（研究 *および* ジャーナルクラブ）。
  * `min_presentations :: Int` (デフォルト, `1`): 各会議日あたりの最小研究発表数。
  * `max_presentations :: Int` (デフォルト, `3`): 各会議日あたりの最大研究発表数。
  * `min_journals :: Int` (デフォルト, `0`): 各会議日あたりの最小ジャーナルクラブ発表数。
  * `max_journals :: Int` (デフォルト, `1`): 各会議日あたりの最大ジャーナルクラブ発表数。
  * `time_limit :: Real` (デフォルト, `60`): オプティマイザに課せられる時間制限（秒単位）；証明可能な最適スケジュールは通常、計算が非現実的に遅くなります。

```
p = profile_solvers(stats, costs, costnames;
                    width = 400, height = 400,
                    b = PlotsBackend(), kwargs...)
```

`stats`のデータに基づいて`solvers`を比較するパフォーマンスプロファイルを生成します。

入力:

  * `stats::Dict{Symbol,DataFrame}`: 各ソルバーのベンチマーク結果を含む`DataFrame`の辞書（例: `bmark_results_to_dataframes()`によって生成されたもの）
  * `costs::Vector{Function}`: プロファイルで使用する測定を指定する関数のベクトル
  * `costnames::Vector{String}`: プロファイルのタイトルとして使用される名前。

キーワード入力:

  * `width::Int`: 各個別プロットの幅（デフォルト: 400）
  * `height::Int`: 各個別プロットの高さ（デフォルト: 400）
  * `b::BenchmarkProfiles.AbstractBackend` : プロットに使用されるバックエンド。

追加の`kwargs`は`plot`呼び出しに渡されます。

出力: ソルバーを比較するパフォーマンスプロファイルのセットを表すPlots.jlプロット。セットには、`costs`で指定された測定に基づいてすべてのソルバーを比較するパフォーマンスプロファイルが含まれます。ソルバーが2つ以上ある場合、各コスト測定に対してソルバーを2つずつ比較する追加のプロファイルが生成されます。

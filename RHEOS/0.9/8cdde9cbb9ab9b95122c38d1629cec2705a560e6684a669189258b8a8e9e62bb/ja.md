```
modelfit(data::RheoTimeData, model::RheoModelClass, modloading::Symbol; p0::Union{NamedTuple,Nothing} = nothing, lo::Union{NamedTuple,Nothing} = nothing, hi::Union{NamedTuple,Nothing} = nothing, verbose::Bool = false, rel_tol_x = 1e-4, diff_method="BD", weights::Union{Vector{Integer},Nothing}=nothing)
```

`RheologyData` 構造体をモデルにフィットさせ、フィットしたモデルを `RheologyModel` オブジェクトとして返します。フィッティングプロセスでは、RHEOSは最適化パッケージ [NLopt](https://nlopt.readthedocs.io/en/latest/) に依存しています。デフォルトでは、RHEOSはローカル導関数フリーアルゴリズム、具体的にはトム・ローワンの「サブプレックス」を使用します。NLoptが使用すべきアルゴリズムを指定するには、キーワードパラメータ `optmethod` を使用し、NLopt.jlで定義された関連するシンボルを提供します。適切なオプションには、ローカル導関数フリー最適化のための `:LN_SBPLX`（デフォルト）、`:LN_COBYLA`、`:LN_BOBYQA` が含まれます。グローバル最適化手法も利用可能ですが、すべてのパラメータに下限と上限の境界を設定する必要があります。これらのアルゴリズムに関する詳細情報は、[NLoptのウェブサイト](https://nlopt.readthedocs.io/en/latest/NLopt_Algorithms/)で入手できます。

# 引数

  * `data`: すべてのデータを含む `RheoTimeData` 構造体
  * `model`: モジュリ関数と名前付きタプルパラメータを含む `RheoModelClass`
  * `modloading`: `strain_imposed` または `1`、`stress_imposed` または `2`
  * `p0`: フィットに使用する初期パラメータ（未定義の場合はすべてのパラメータに0.5を使用）、名前付きタプルとして提供
  * `lo`: パラメータの下限、名前付きタプルとして提供
  * `hi`: パラメータの上限、名前付きタプルとして提供
  * `verbose`: trueの場合、各最適化反復でパラメータを印刷
  * `rel_tol_x`: 入力パラメータ値の関数としての最適化の相対許容誤差、詳細についてはNLOptのドキュメントを参照
  * `rel_tol_f`: 指定された場合、関数値の変化に基づく基準を設定
  * `diff_method`: 導関数に使用する有限差分公式を設定、現在は `"BD"` または `"CD"`
  * `weights`: 重要性に応じて重み付けされたインデックスのベクター、`indexweight` 関数によって生成可能
  * `optmethod`: NLOptによって使用される最適化アルゴリズム（シンボルまたは文字列として渡される）
  * `opttimeout`: ユーザーが最適化の壁時計タイムアウトを設定できるようにし、失敗した最適化を停止して安全に戻るために使用
  * `optmaxeval`: ユーザーが最適化中の評価の最大数を設定できるようにし、再現性が必要な場合に使用

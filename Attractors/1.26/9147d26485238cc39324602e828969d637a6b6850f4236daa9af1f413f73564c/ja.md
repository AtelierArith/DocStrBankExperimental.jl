```
global_continuation(gca::GlobalContinuationAlgorithm, prange, pidx, ics; kwargs...)
global_continuation(gca::GlobalContinuationAlgorithm, pcurve, ics; kwargs...)
```

引き寄せ子（または引き寄せ子の表現）を見つけて続け、与えられた初期条件 `ics` に従ってパラメータ範囲 `pcurve` 全体にわたる引き寄せ子の領域の割合を求めます。

返すもの：

1. `fractions_cont::Vector{Dict{Int, Float64}}`。引き寄せ子の領域の割合。`fractions_cont[i]` は、`i` 番目のパラメータの組み合わせにおける引き寄せ子 ID からその領域の割合への辞書です。

      * この出力は、[`StabilityMeasuresAccumulator`](@ref) と [`AttractorSeedContinueMatch`](@ref) を組み合わせて使用している場合に異なります。詳細については、[`StabilityMeasuresAccumulator`](@ref) のドキュメントを参照してください。
2. `attractors_cont::Vector{Dict{Int, <:Any}}`。続けられた引き寄せ子。`attractors_cont[i]` は、`i` 番目のパラメータの組み合わせにおける引き寄せ子 ID から引き寄せ子セットへの辞書です。

出力を別の形式に変換したい場合は、関数 [`continuation_series`](@ref) を参照してください。

## キーワード引数

  * `show_progress = true`: 計算の進行状況を表示するプログレスバー。
  * `samples_per_parameter = 100`: `ics` が初期条件のセットではなく関数である場合、各パラメータの組み合わせでサンプリングされる初期条件の数。

## 説明

`global_continuation` は、[Datseris2023](@cite) で示されるグローバル安定性分析のフレームワークの中心的な関数です。

グローバル継続アルゴリズムは通常、動的システムの引き寄せ子と領域を見つけるために使用される [`AttractorMapper`](@ref) を参照します。引き寄せ子をパラメータ範囲全体で続ける/追跡する/一致させる方法を制御する追加の引数は、`gca` を作成する際に指定されます。

領域の割合と引き寄せ子（またはそのいくつかの表現）は、システムのパラメータインデックス `pidx` に対して、パラメータ範囲 `prange` 全体で続けられます（`DynamicalSystems.set_parameter!` で有効な任意のインデックスを使用できます）。従来の継続と対照的に（比較のためのオンラインチュートリアルを参照）、グローバル継続はパラメータ空間内の任意のユーザー定義の曲線にわたって実行できます。`pcurve` を使用した2番目の呼び出しシグネチャは、この可能性を許可します。この場合、`pcurve` はイテラブルのベクターであり、各イテラブルはパラメータインデックスをパラメータ値にマッピングします。これらのイテラブルは辞書、名前付きタプル、`Vector{Pair}` などであり、イテラブルのシーケンスがパラメータ空間内の曲線を定義します。実際、`prange, pidx` を使用したバージョンは単に `pcurve = [[pidx => p] for p in prange]` を定義し、2番目のメソッドを呼び出します。

`ics` は、グローバルに状態空間をサンプリングする際に使用する初期条件です。[`basins_fractions`](@ref) と同様に、初期条件のセットベクターであるか、ランダムな初期条件を生成する0引数の関数であることができます。

`GlobalContinuationAlgorithm` の可能なサブタイプは次のとおりです：

  * [`AttractorSeedContinueMatch`](@ref)
  * [`FeaturizeGroupAcrossParameter`](@ref)

```

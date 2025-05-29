```
result::StatsBase.Histogram =
    partial_cmd_smooth(m_ini::AbstractVector{<:Number},
                       mags::AbstractVector{<:AbstractVector{<:Number}},
                       mag_err_funcs,
                       y_index,
                       color_indices,
                       imf,
                       completeness_funcs=[one for i in mags];
                       dmod::Number=0,
                       normalize_value::Number=1,
                       binary_model::AbstractBinaryModel=NoBinaries(),
                       mean_mass=mean(imf),
                       edges=nothing,
                       xlim=nothing,
                       ylim=nothing,
                       nbins=nothing,
                       xwidth=nothing,
                       ywidth=nothing)

単純な星の集団からのテンプレートヘス図を生成するための主関数で、イソクローネからの星を含み、光学的誤差と完全性を考慮します。

# 引数

  * `m_ini::AbstractVector{<:Number}` は、イソクローネからの星の初期星質量を含むベクトルです。
  * `mags::AbstractVector{<:AbstractVector{<:Number}}` はベクトルのベクトルです。各構成ベクトルのインデックス `i` は `length(mags[i]) == length(m_ini)` である必要があり、考慮される各光度におけるイソクローネ星の光度を表します。ほとんどの場合、mags には 2（y 軸の光度が x 軸の色にも関与している場合）または 3 のベクトルが含まれるべきです。
  * `mag_err_funcs` は、`mags` で提供される同じフィルターの 1σ 光学的誤差を計算するための呼び出し可能なオブジェクト（例：`Vector` または `Tuple`）でなければなりません。各呼び出し可能な関数は単一の引数（*見かけの* 光度）を取り、`Number` を返す必要があります。`mag_err_funcs` の長さは `mags` の長さと等しくなければなりません。
  * `y_index` は、ヘス図の y 軸に持ちたいフィルターのための `mags` への有効なインデックス（例：`Int` または `CartesianIndex`）を提供します。例えば、`mags` 引数が B および V バンドの光度を `mags=[B, V]` として含み、y 軸に V を持ちたい場合、`y_index` を `2` に設定します。
  * `color_indices` は、x 軸の色を計算するために使用される `mags` へのインデックスを提供する長さ 2 のインデックス可能なオブジェクトです。例えば、`mags` 引数が B および V バンドの光度を `mags=[B, V]` として含み、B-V を x 軸の色にしたい場合、`color_indices` は `[1,2]` または `(1,2)` またはそれに類似したものにする必要があります。
  * `imf` は、初期星質量を唯一の引数として受け取り、初期質量関数モデルの（適切に正規化された）確率密度を返す呼び出し可能な関数です。[InitialMassFunctions.jl](https://github.com/cgarling/InitialMassFunctions.jl) のすべてのモデルは `imf` に対して有効です。
  * `completeness_functions` は、*見かけの* 光度の関数として単一フィルターの完全性比を計算するための呼び出し可能なオブジェクト（例：`Vector` または `Tuple`）でなければなりません。この引数の各呼び出し可能な関数は、`mags` で提供される対応するフィルターに対応する必要があります。

# キーワード引数

  * `dmod::Number=0` は、入力 `mags` に適用する光度の距離モジュラスです。`mags` に見かけの光度を提供している場合は `0` のままにします。
  * `normalize_value::Number=1` は、モデル化したい集団の総星質量です。
  * `binary_model::AbstractBinaryModel=NoBinaries()` は、二重系を含めるために使用するモデルです。現在、[`StarFormationHistories.NoBinaries`](@ref) と [`StarFormationHistories.RandomBinaryPairs`](@ref) のみがサポートされています。
  * `mean_mass::Number` は、提供された `imf` から引き出されたランダムな星の初期質量の期待値です。提供された `imf` が有効な連続の単変量 `Distributions.Distribution` オブジェクトである場合、これが計算されます。
  * `edges` は、x 軸（`edges[1]`）および y 軸（`edges[2]`）に沿ったビンの左側のエッジを定義する範囲のタプルです。例：`(-1.0:0.1:1.5, 22:0.1:27.2)`。`edges` が提供されると、ヘス図の範囲を指定する他の方法を提供する以下のキーワード引数を上書きします。
  * `xlim` は、提供された `colors` 配列に対応する x 軸の下限と上限を与える長さ 2 のインデックス可能なオブジェクト（例：`Vector` または `Tuple`）です。例：`(-1.0, 1.5)`。これは `edges` が提供されていない場合にのみ使用されます。
  * `ylim` は、提供された `mags` 配列に対応する y 軸のための `xlim` と同様です。例 `(25.0, 20.0)`。これは `edges` が提供されていない場合にのみ使用されます。
  * `nbins::NTuple{2, <:Integer}` は、x 軸および y 軸に沿って使用するビンの数を提供する整数の 2 タプルです。これは `edges` が提供されていない場合にのみ使用されます。
  * `xwidth` は、`colors` 配列の x 軸に沿ったビンの幅です。これは `edges` と `nbins` が提供されていない場合にのみ使用されます。例：`0.1`。
  * `ywidth` は、提供された `mags` 配列に対応する y 軸のための `xwidth` と同様です。例：`0.1`。

# 戻り値

このメソッドは、`StatsBase.Histogram` としてヘス図を返します。詳細については、StatsBase のドキュメントを参照してください。簡単に言うと、このメソッドの出力が `result` である場合、`result.weights` として表されるヘス図は `Matrix` として利用可能であり（これは [`fit_templates`](@ref) や類似の関数に必要なものです）、ヒストグラムのエッジは `result.edges` として利用可能です。
```

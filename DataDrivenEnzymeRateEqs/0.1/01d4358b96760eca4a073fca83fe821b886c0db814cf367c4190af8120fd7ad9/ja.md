```
data_driven_rate_equation_selection(
    general_rate_equation::Function,
    data::DataFrame,
    metab_names::Tuple{Symbol,Vararg{Symbol}},
    param_names::Tuple{Symbol,Vararg{Symbol}};
    range_number_params::Union{Nothing, Tuple{Int,Int}} = nothing,
    forward_model_selection::Bool = true,
    max_zero_alpha::Int = 1 + ceil(Int, length(metab_names) / 2),
    n_reps_opt::Int = 20,
    maxiter_opt::Int = 50_000,
    model_selection_method::String = "current_subsets_filtering",
    p_val_threshold::Float64 = 0.4,
    save_train_results::Bool = false,
    enzyme_name::String = "Enzyme",
    subsets_min_limit::Int = 1,
    subsets_max_limit::Union{Int, Nothing}=nothing,
    subsets_filter_threshold::Float64=0.1,
)
```

この関数は、一般的な反応速度方程式とデータを使用してデータ駆動型の反応速度方程式選択を実行するために使用されます。

モデル選択方法は3つあります：

1. current*subsets*filtering:

この方法は、前の反復からの上位10％のサブセットのモデルを反復的にフィットさせ、トレーニング損失に基づいて各nパラメータの最良モデルを保存します。最適なパラメータ数は、LOOCVからのテストスコアに対するウィルコクソン検定を使用して選択され、最良の方程式はこの最適な数を持つ最良モデルです。

2. cv*subsets*filtering:

この方法は、各図に対してcurrent*subsets*filteringを別々に実装し、1つの図をテストセットとして残し、残りのデータでトレーニングします。各パラメータ数に対して、その図の最良サブセットのテスト損失を保存します。すべての図の結果に対してウィルコクソン検定を使用して最適なパラメータ数を選択します。次に、選択された数に対して、全データセットでこのnパラメータを使用してすべてのサブセットをトレーニングし、最小のトレーニング損失に基づいて最良の反応速度方程式を選択します。

3. cv*all*subsets:

この方法は、各図に対してすべてのサブセットをフィットさせ、他の図をトレーニングデータとして使用し、残された図をテストセットとして使用します。各パラメータ数と図に対してトレーニングエラーに基づいて最良モデルを選択し、LOOCVテストスコアを計算します。最適なnパラメータは、すべての図のテストスコアに対するウィルコクソン検定によって決定されます。最良の方程式は、全データセットでトレーニングされたこの最適なnパラメータの最小トレーニング損失を持つサブセットです。

# 引数

  * `general_rate_equation::Function`: メタボライト濃度（`metab_names`キー）とパラメータ（`param_names`キー）のNamedTupleを受け取り、酵素速度を返す関数。
  * `data::DataFrame`: 列`Rate`と各`metab_names`の列を含むデータフレームで、各行は1つの測定値です。また、データのソースを識別する文字列を含む`source`列も必要です。これは、出版物の各図の重みを計算するために使用されます。
  * `metab_names::Tuple`: `rate_equation`のメタボライトに対応するメタボライト名のタプルで、`data`の列名に対応します。
  * `param_names::Tuple`: `rate_equation`のパラメータに対応するパラメータ名のタプルです。

# キーワード引数

  * `save_train_results::Bool`: 各パラメータ数のトレーニング結果をcsvファイルとして保存するかどうかを示すブール値。
  * `enzyme_name::String`: 保存されるcsvファイルの名前に使用される酵素名の文字列。
  * `range_number_params::Tuple{Int,Int}`: 一般的な*rate*equationのパラメータ数の範囲を表す整数のタプル。
  * `forward_model_selection::Bool`: フォワードモデル選択（true）またはリバースモデル選択（false）を使用するかどうかを示すブール値。
  * `max_zero_alpha::Int`: 0に設定できるアルファパラメータの最大数を表す整数。
  * `n_reps_opt::Int` 最適化の繰り返し回数
  * `maxiter_opt::Int` 最適化アルゴリズムの最大反復回数
  * `model_selection_method::String` - 最良の反応速度方程式を見つけるためのモデル選択（デフォルトはcurrent*subsets*filtering）
  * `p_val_threshold::Float64` - ウィルコクソン検定のpval閾値
  * `save_train_results::Bool`: 各パラメータ数のトレーニング結果をcsvファイルとして保存するかどうかを示すブール値。
  * `enzyme_name::String`: 保存されるcsvファイルの名前に使用される酵素名の文字列。
  * `subsets_min_limit::Int` - 各パラメータ数のために保持されるべきフィルタリングされたサブセットの最小数（トレーニング損失が最小の10％以内のもの）。

これらのサブセットは、次の反復のためのサブセットを生成するために使用されます（これらのサブセットのサブセットのみが考慮されます）。モデル選択方法current*subsets*filteringまたはcv*subsets*filteringに関連しています。

  * `subsets_max_limit::Union{Int, Nothing}` - 各パラメータ数のために保持されるべきフィルタリングされたサブセットの最大数（トレーニング損失が最小の10％以内のもの）。

これらのサブセットは、次の反復のためのサブセットを生成するために使用されます（これらのサブセットのサブセットのみが考慮されます）。モデル選択方法current*subsets*filteringまたはcv*subsets*filteringに関連しています。

  * `subsets_filter_threshold::Float64` - 各反復でサブセットをフィルタリングするためのパーセンテージ制限を設定します。

トレーニング損失が最良に近い（このパーセンテージ以内）のサブセットのみが保持されます。モデル選択方法current*subsets*filteringまたはcv*subsets*filteringに関連しています。

# 戻り値

  * `NamedTuple`: 次のフィールドを持つ名前付きタプル：

      * `results`: トレーニングとテストの結果を含むデータフレーム
      * `best_n_params`: 最適なパラメータ数
      * `best_subset_row`: 選択された最良の反応速度方程式の行 - フィットしたパラメータを含む

```

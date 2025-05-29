```julia
get_matrix_params(
    param_dict,
    layer_name,
    expected_size;
    matrix_name,
    bias_name
)

```

行列の乗算を行うレイヤー（例：全結合層 / ソフトマックス層）のパラメータを `param_dict` から [`Linear`](@ref) オブジェクトとしてインポートするためのヘルパー関数です。

キーのデフォルト形式は `'layer_name/weight'` と `'layer_name/bias'` であり、`matrix_name` と `bias_name` という名前付き引数を渡すことでカスタマイズできます。期待されるパラメータ名は `'layer_name/matrix_name'` と `'layer_name/bias_name'` になります。

# 引数

  * `param_dict::Dict{String}`: パラメータ名を重み / バイアスの配列にマッピングする辞書。
  * `layer_name::String`: 辞書内のパラメータを識別します。
  * `expected_size::NTuple{2, Int}`: レイヤーの重みに対する期待されるサイズに対応する長さ2のタプル。

```
unmix_pixel(library::SpectralLibrary, img_dat_input::Array{Float64}, unc_dat,
            class_idx, options, mode::String, n_mc::Int64,
            num_endmembers::Vector{Int64}, normalization::String, optimization::String,
            max_combinations::Int64, combination_type::String)
```

与えられたスペクトルライブラリを使用して、SMAまたはMESMAのオプションとさまざまなモンテカルロおよび最適化アプローチを使用して、ピクセルのスペクトルデータをアンミックスします。

# 引数

  * `library::SpectralLibrary`: アンミックス用のエンドメンバーライブラリ。
  * `img_dat_input::Array{Float64}`: ピクセルのスペクトルデータ。
  * `unc_dat`: ピクセルのスペクトルデータの不確実性のオプション配列。
  * `class_idx`: `library.spectra`内の異なるエンドメンバーのクラスメンバーシップを示すインデックスのコレクション。 [`prepare_combinations`](@ref)、[`prepare_options`](@ref)も参照してください。
  * `options`: アンミックスプロセスのための潜在的なエンドメンバーの組み合わせのコレクション。 [`prepare_options`](@ref)も参照してください。
  * `mode::String`: アンミックスアプローチを決定します：

      * `"sma"`: MCアンミックスのためにエンドメンバーをランダムに選択し、平均分数を返します。
      * `"sma-best"`: SMAを使用し、最良（コストが最も低い）MC分数を出力します。
      * `"mesma"`: 各クラスを表すエンドメンバーの異なる組み合わせを評価します。
      * `"mesma-best"`: MESMAを使用し、最良（コストが最も低い）MC分数を出力します。
  * `n_mc::Int64`: MCイテレーションの数。
  * `num_endmembers::Vector{Int64}`: 考慮すべきエンドメンバーの数。
  * `normalization::String`: スペクトルデータに適用する正規化方法。 [`scale_data`](@ref)を参照してください。
  * `optimization::String`: アンミックスのための最適化アプローチ：（例：`"bvls"`、`"ldsqp"`、または`"inverse"`）。 適用可能な場合、逆方法を指定するために`"pinv"`または`"qr"`を含むことができます。
  * `max_combinations::Int64`: 考慮すべき最大組み合わせ数。
  * `combination_type::String`: 組み合わせのタイプ（例：`"class-even"`）。 [`prepare_combinations`](@ref)、[`prepare_options`](@ref)、[`get_sma_permutation`](@ref)も参照してください。

# 戻り値

  * 次の内容を含むタプル：

      * `output_mixture::Vector{Float64}`: `library`内の各クラスの推定分数で、明るさが追加されています。
      * `output_mixture_var::Vector{Float64}`: `library`内の各クラスの分散で、明るさの分散が追加されています。
      * `output_comp_frac::Vector{Float64}`: `library`内の各エンドメンバーの推定分数で、明るさが追加されています。
      * `output_comp_frac_var::Vector{Float64}`: `library`内の各エンドメンバーの分散で、明るさの分散が追加されています。

```

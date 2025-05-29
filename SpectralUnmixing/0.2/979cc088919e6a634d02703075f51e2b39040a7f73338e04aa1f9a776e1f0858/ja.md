```
unmix_line(line::Int64, reflectance_file::String, mode::String,
            refl_nodata::Float64, refl_scale::Float64,
            normalization::String, library::SpectralLibrary,
            reflectance_uncertainty_file::String="", n_mc::Int64=1,
            combination_type::String="all",
            num_endmembers::Vector{Int64}=[2, 3],
            max_combinations::Int64=-1, optimization="bvls")
```

特定の行（ピクセルの行）の反射データをアンミックスします。詳細は [`load_line`](@ref)、[`unmix_pixel`](@ref) を参照してください。

# 引数

  * `line::Int64`: アンミックスする行のインデックス。
  * `reflectance_file::String`: 反射データへのパス。
  * `mode::String`: 使用するアンミックスのモード（例："sma", "mesma-best"）。詳細は

[`unmix_pixel`](@ref) を参照してください。

  * `refl_nodata::Float64`: 反射ファイルのノーデータ値。
  * `refl_scale::Float64`: 反射データのスケーリングファクター。
  * `normalization::String`: 反射データに適用する正規化方法。詳細は

[`scale_data`](@ref) を参照してください。

  * `library::SpectralLibrary`: アンミックス用のエンドメンバーを含むスペクトルライブラリオブジェクト。
  * `reflectance_uncertainty_file::String`: 反射不確実性ファイルへのオプションのパス。
  * `n_mc::Int64=1`: 実行するモンテカルロ反復の数。
  * `combination_type::String="all"`: アンミックスのために準備するエンドメンバーの組み合わせのタイプ。詳細は

[`prepare_combinations`](@ref)、[`prepare_options`](@ref) を参照してください。

  * `num_endmembers::Vector{Int64}=[2, 3]`: 組み合わせで考慮するエンドメンバーの数。
  * `max_combinations::Int64=-1`: 考慮する最大組み合わせ数、デフォルトは制限なし。
  * `optimization::String`: 使用する最適化方法（デフォルトは "bvls"）。詳細は

[`unmix_pixel`](@ref) を参照してください。

# 戻り値

  * タプルを返します（詳細は [`unmix_pixel`](@ref) を参照）：

      * 行インデックス。
      * 行内の各ピクセルの推定クラス比率。
      * 有効データを持つピクセルのブールマスク。
      * 混合結果の標準偏差（該当する場合）。
      * 各ピクセルのアンミックスにおける各エンドメンバーの完全な比率。

# 注意事項

  * 再現性のためにランダムシードを初期化します。
  * 行のアンミックスの実行時間をログに記録します。
  * 入力データが無効または欠落している場合は `nothing` を返します。

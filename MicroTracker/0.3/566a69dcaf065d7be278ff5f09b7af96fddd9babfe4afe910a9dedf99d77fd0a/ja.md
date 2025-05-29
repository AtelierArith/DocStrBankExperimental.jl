```
trajectory_analyzer(linked_data, collapsed_data, particle_unique::AbstractString, [framenumber; [size_variable="Major_um"], [annotationkwargs...])
```

単一のマイクロボットの包括的なダッシュボードを表示し、瞬時の速度、選択した `size_variable`、および `size_variable` のFFTを含みます。

# 引数

  * `linked_data` : `AbstractDataFrame`、[`load_linked_data`](@ref) または [`batch_particle_data_to_linked_data`](@ref) によって返される時系列リンクデータ。
  * `collapsed_data` : `AbstractDataFrame`、[`collapse_data`](@ref) によって返されるマイクロボットごとの行を持つ圧縮データ。
  * `particle_unique` : `AbstractString`。分析対象のマイクロボットの一意の識別子。
  * `framenumber` : (オプション) `Int` 表示するフレーム番号。指定されていない場合、最後のフレームが使用されます。
  * `size_variable` : (オプション) `AbstractString`、表示するサイズ変数の列名。デフォルトは `"Major_um"`。
  * `annotationkwargs` : (オプション) [`plotannotatedframe_single()`](@ref) に渡されるキーワード引数。

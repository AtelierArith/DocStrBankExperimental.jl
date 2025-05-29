```
animate_trajectory_analyzer(linked_data, collapsed_data, particle_unique, savepath, [framerange]; animation_speed_multiplier=1, size_variable="Major_um", annotationkwargs...)
```

軌道アナライザーのアニメーションをエクスポートし、`savepath`に保存します。

# 引数

  * `linked_data` : `AbstractDataFrame`、[`load_linked_data`](@ref)または[`batch_particle_data_to_linked_data`](@ref)によって返される、時系列リンクデータ。
  * `collapsed_data` : `AbstractDataFrame`、[`collapse_data`](@ref)によって返される、マイクロボットごとの行を持つ折りたたまれたデータ。
  * `particle_unique` : `AbstractString`。分析対象のマイクロボットの一意の識別子。
  * `savepath` : `AbstractString`。アニメーションを保存するパス。
  * `framerange` : (オプション) `UnitRange{Int64}`。表示するフレームの範囲。指定しない場合、全体の軌道がアニメーション化されます。
  * `animation_speed_multiplier` : (オプション) `Int`。アニメーションの速度。デフォルトは1。
  * `size_variable` : (オプション) `AbstractString`、表示するサイズ変数の列名。デフォルトは`"Major_um"`。
  * `annotationkwargs` : (オプション) [`plotannotatedframe_single()`](@ref)に渡されるキーワード引数。

# 例

```julia-repl
julia> trajectory_analyzer(linked_data, collapsed_data, "5_13p5_61p35-2", "my_animation.mp4")
[ Info: Creating animation: Frame = 5
...
[ Info: Saved animation to ~/my_animation.mp4
```

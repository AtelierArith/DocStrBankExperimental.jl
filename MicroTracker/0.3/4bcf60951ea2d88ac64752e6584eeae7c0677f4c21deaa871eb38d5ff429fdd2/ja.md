```
link(particle_data::AbstractDataFrame, linking_settings::NamedTuple; trackpykwargs...)
```

粒子データをフレーム間で軌跡にリンクするためにtrackpyを使用します。

`linking_settings`のフィールドとフォーマットについては、[Linking Settings](@ref) ドキュメントを参照してください。任意のkwargsはtrackpy.link関数 [trackpy.link](https://soft-matter.github.io/trackpy/v0.6.1/generated/trackpy.link.html#trackpy.link) に渡されます。

# 例

```julia-repl
julia> link(particle_data, linking_settings)
```

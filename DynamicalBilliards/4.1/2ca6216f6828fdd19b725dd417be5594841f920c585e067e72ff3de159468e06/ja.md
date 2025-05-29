```
bdplot_video(file::String, bd::Billiard, ps::Vector{<:AbstractParticle}; kwargs...)
```

`ps`が`bd`の中で進化するアニメーションを作成し、それを`file`に保存します。この関数は、[`bdplot_interactive`](@ref)とすべての視覚化関連のキーワードを共有しています。他のキーワードは次のとおりです：

  * `steps = 10`: 新しいフレームを生成する間に取られる`dt`ステップの数。
  * `frames = 1000`: 合計で生成するフレームの数。
  * `framerate = 60`。

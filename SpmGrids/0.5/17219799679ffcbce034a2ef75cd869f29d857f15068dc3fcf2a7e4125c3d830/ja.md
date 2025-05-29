```
plot_plane(grid::SpmGrid, response_channel::String,
    x_index::GridRange, y_index::GridRange, channel_index::GridRange=:;
    bwd::Bool=false, ax::Any=nothing, backend::Module=Main,
    kwargs...)::NamedTuple
```

`response_channel`の平面を、x,y平面とスイープ信号によって広がる三次元データにプロットします。インデックスは`x_index`、`y_index`、`channel_index`を通じて行われ、二次元配列が得られるようにする必要があります。`bwd`が`true`に設定されている場合、存在する場合は後方スイープのデータがプロットされます。

この関数を使用する前に、[Makie](https://makie.juliaplots.org/)バックエンド（`GLMakie`、`CairoMakie`または`WGLMakie`）をインポートし、図または軸を設定する必要があります。特定のAxisは`ax`キーワード引数を介して指定できます。デフォルトでは、`Main`モジュールのMakieバックエンドが使用されますが、`backend`キーワード引数を介して直接指定することもできます。

追加のキーワード引数を指定でき、プロット関数に渡されます。

ヒートマップ、カラーバーラベル、およびプロットラベルを含むNamedTupleを返します。

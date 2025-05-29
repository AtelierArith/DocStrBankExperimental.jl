```
plot_line(grid::SpmGrid, response_channel::String,
    x_index::GridRange, y_index::GridRange, channel_index::GridRange=nothing;
    sweep_channel::String="", bwd::Bool=true, ax::Any=nothing, backend::Module=Main,
    kwargs...)::NamedTuple
```

`response_channel`をx,y平面と分光データによって広がる三次元データのラインに沿ってプロットします。インデックスは`x_index`、`y_index`、`channel_index`を通じて行われ、一次元配列が得られるようにする必要があります。また、グリッド内の1点に対して`sweep_channel`（指定されていない場合はスイープ信号がデフォルト）に対する`response_channel`をプロットすることも可能です。`bwd`が`true`（デフォルト）の場合、プロットには後方スイープからのデータも含まれます（存在する場合）。

この関数を使用する前に、[Makie](https://makie.juliaplots.org/)バックエンド（`GLMakie`、`CairoMakie`または`WGLMakie`）をインポートし、図または軸を設定する必要があります。特定のAxisは`ax`キーワード引数を介して指定できます。デフォルトでは、`Main`モジュールからのMakieバックエンドが使用されますが、`backend`キーワード引数を介して直接指定することもできます。

追加のキーワード引数を指定でき、プロット関数に渡されます。接尾辞`_bwd`を持つキーワード引数は、後方スキャンのプロットに使用されます。    

NamedTupleを返します。

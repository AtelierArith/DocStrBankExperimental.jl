```
plot_spectrum(grid::SpmGrid, sweep_channel::String, response_channel::String,
    x_index::GridRange, y_index::GridRange, channel_index::GridRange=:;
    bwd::Bool=true, ax::Any=nothing, backend::Module=Main,
    kwargs...)::NamedTuple
```

`sweep_channel`に対する`response_channel`の線グラフを、指定された`x_index`と`y_index`上にプロットします。`sweep_channel`が`""`の場合、スイープ信号が`sweep_channel`として使用されます。さらに、スペクトルデータは`channel_index`でインデックス指定できます。`bwd`が`true`（デフォルト）の場合、プロットには後方スイープのデータも含まれます（存在する場合）。

この関数を使用する前に、[Makie](https://makie.juliaplots.org/)バックエンド（`GLMakie`、`CairoMakie`、または`WGLMakie`）をインポートし、図または軸を設定する必要があります。特定の軸は`ax`キーワード引数を介して指定できます。デフォルトでは、`Main`モジュールのMakieバックエンドが使用されますが、`backend`キーワード引数を介して直接指定することもできます。

追加のキーワード引数を指定でき、プロット関数に渡されます。サフィックス`_bwd`を持つキーワード引数は、後方スキャンのプロットに使用されます。

NamedTupleを返します。

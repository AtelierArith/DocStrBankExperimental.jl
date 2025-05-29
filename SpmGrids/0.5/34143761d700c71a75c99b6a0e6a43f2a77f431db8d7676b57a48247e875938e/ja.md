plot*parameter*plane(grid::SpmGrid, parameter::String,         x*index::GridRange=:, y*index::GridRange=:;         ax::Any=nothing, backend::Module=Main,         kwargs...)::NamedTuple

`parameters`の値をx,y平面の関数としてプロットします。インデックスは`x_index`、`y_index`を通じて行われます。

この関数を使用する前に、[Makie](https://makie.juliaplots.org/)バックエンド（`GLMakie`、`CairoMakie`または`WGLMakie`）をインポートし、図または軸を設定する必要があります。特定のAxisは`ax`キーワード引数を介して指定できます。デフォルトでは、`Main`モジュールからのMakieバックエンドが使用されます。また、`backend`キーワード引数を介して直接指定することもできます。

追加のキーワード引数を指定でき、プロット関数に渡されます。

ヒートマップ、カラーバーラベル、およびプロットラベルを含むNamedTupleを返します。
